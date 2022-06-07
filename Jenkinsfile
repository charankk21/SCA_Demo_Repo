pipeline{
    agent any
    stages{
	name: Snyk SCA Scan

on:
  push:
    branches: [ test ]
  pull_request:
    branches: [ test ]

jobs:
  snyk-scan:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Set up JDK 11
        uses: actions/setup-java@v2
        with:
          java-version: '11'
          distribution: 'adopt'
      - name: Build with Maven
        run: mvn -B package --file pom.xml
      - name: run MVN install
        run: mvn install # install maven

      - uses: actions/setup-node@v2
        with:
          node-version: '14'
      - run: npm install snyk -g # install snyk
      - run: snyk -v
      - run: snyk auth ${{ secrets.test }} # snyk authentication using GH secrets
      - run: snyk monitor

        # Generate the HTML report
      - name: Run snyk test and install snyk-to-html
        run: | 
         npm install snyk-to-html -g
               # Convert JSON output from `snyk test --json` into a static HTML
         snyk test --json | snyk-to-html -o result.html
         mkdir downloads
         pwd
         cp -v /home/runner/*/*/*/*.html /home/runner/work/*/*/downloads
      # save the HTML in the artifact
      - name: Use the Upload Artifact GitHub Action
        uses: actions/upload-artifact@v2
        with:
          name: results
          path: downloads
	}
}
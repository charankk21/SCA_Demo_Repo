pipeline{
    agent any
    stages{
	stage('SCA-->Snyk') {
            agent any
            steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/charankk21/TruffleTest.git']]])
				snykSecurity failOnIssues: false, organisation: '35c65e0d-af9d-4ed5-9caf-db0821e2f219', snykInstallation: 'snykKey', snykTokenId: 'snykSecrectS'
                }
        }
	}
}

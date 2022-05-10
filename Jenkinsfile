pipeline{
    agent none
    stages{
stage('SCA-->Snyk') {
            agent any
            steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/']], extensions: [], userRemoteConfigs: [[url: '']]])
				snykSecurity failOnIssues: false, organisation: '', snykInstallation: '', snykTokenId: ''
                }
        }
	}
}
pipeline{
    agent any
    stages{
	stage('SCA-->Snyk') {
            agent any
            steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/charankk21/SCA_Demo_Repo.git']]])
				snykSecurity failOnIssues: false, organisation: '0fc86b5d-38a2-4a8f-9f5e-90b2c2dec1b1', snykInstallation: 'snykKey', snykTokenId: 'CK_SNYK_TOKEN'
                }
        }
stage('snyk-jira') {
		steps {
			script{
				catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') 
				{
					bat 'C:\\Users\\Administrator\\Downloads\\snyk-jira-sync-win.exe --orgID=ea0871ca-05d5-4005-b34a-59f732ba9bb3 --token=CK_SNYK_TOKEN --jiraProjectKey=SNYK --configFile=true --jiraTicketType=Task --projectID=$projectID$'
					bat 'exit 0'
				}
			}
		}
	}
	}
}
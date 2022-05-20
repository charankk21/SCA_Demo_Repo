pipeline{
    agent any
    stages{
	stage('SCA-->Snyk') {
            agent any
            steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/charankk21/SCA_Demo_Repo.git']]])
				snykSecurity failOnIssues: false, organisation: '5fa845f1-b5bc-4ae1-8c00-dffe4ace79f7', snykInstallation: 'snykKey', snykTokenId: 'CK_SNYK_TOKEN'
                }
        }
stage('snyk-jira') {
		steps {
			script{
				catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') 
				{
					bat 'C:\\Users\\Administrator\\Downloads\\snyk-jira-sync-win.exe --orgID=5fa845f1-b5bc-4ae1-8c00-dffe4ace79f7 --token=CK_SNYK_TOKEN --jiraProjectKey=SNYK --configFile=true --jiraTicketType=Task --projectID=1e30db1e-9896-43b7-b9ad-df71bcf6ac7c'
					bat 'exit 0'
				}
			}
		}
	}
	}
}

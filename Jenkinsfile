node{


stage('SetEnv') {
checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/charankk21/SCA_Demo_Repo.git']]])

}



stage('Snyk'){
snykSecurity failOnIssues: false, organisation: '0fc86b5d-38a2-4a8f-9f5e-90b2c2dec1b1', snykInstallation: 'snykKey', snykTokenId: 'CK_SNYK_TOKEN'

}



}
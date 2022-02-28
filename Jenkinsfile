pipeline{
	agent any 
	stages{
		stage('git-clone'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '59e31795-fdc3-42f9-ba89-2701d5610636', url: 'https://github.com/yvanebo30/module2_ci.git']]])
			}
		}
	}
}

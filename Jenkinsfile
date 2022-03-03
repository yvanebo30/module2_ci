pipeline{
	agent any
	tools {maven 'maven'}
	stages{
		stage('git-clone'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'cf9ef057-509b-4047-a397-13a74b755f47', url: 'https://github.com/yvanebo30/module2_ci.git']]])
			}
		}
		stage('etech-hello'){
			steps{
				sh 'git version'
			}
		}
		stage('Build Artifact - Maven') {
      steps {
        sh "mvn clean package -DskipTests=true"
        archive 'target/*.jar'
      }
   }
	}
}

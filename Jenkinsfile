pipeline{
	agent any 
	tools { maven 'maven'}
	stages{
		stage('git-clone'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '59e31795-fdc3-42f9-ba89-2701d5610636', url: 'https://github.com/yvanebo30/module2_ci.git']]])
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
     stage('Unit Tests - JUnit and JaCoCo') {
      steps {
        sh 'mvn test'
      }
      post {
        always {
          junit 'target/surefire-reports/*.xml'
          jacoco execPattern: 'target/jacoco.exec'
        }
      }
    }
  }
}

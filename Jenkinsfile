pipeline {
    agent any
    tools {
      maven 'mvn-3.8.4'
    }
    stages {
        stage (checkout) {
            steps {
                git credentialsId: 'git-cred', url: 'https://github.com/vinodkumar501/VND-hello-world-java-pom.xml.git'
		//checkout([$class: 'GitSCM', branches: [[name: 'refs/heads/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-cred', url: 'https://github.com/vinodkumar501/VND-ITRACK-JENKINSFILE-CICD-DEC2021.git']]])
            }
        }
        stage (build) {
            steps {
                sh "mvn clean install"       //sh "mvn clean install -f mywebapp/prox.xml"   If pom.xml not in root folder
            }
        }
        stage (sonarqube_analysis) {
           steps {
              withSonarQubeEnv(credentialsId: 'sonarqube-cred', installationName: 'sonarqube-9') {            // You can override the credential to be used
			  sh 'mvn sonar:sonar'           //sh "mvn sonar:sonar -f mywebapp/prox.xml"   If pom.xml not in root folder
               //sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
              }
        } 
        //stage ('DEV Approve') {
          // steps {
           //  echo "Taking approval from DEV Manager for QA Deployment"
           // timeout(time: 7, unit: 'DAYS') {
            // input message: 'Do you want to deploy?', submitter: 'admin'
         // }
        //}
      //}	
		
    }    
	
  }
}

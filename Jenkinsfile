pipeline {
    agent any
    //tools {
        //maven 'mvn-3.8.4'                    //automatic install of maven using jenkinsUI use like tools
    //}
    environment {
        PATH = "/opt/maven-3/bin:$PATH"        //manual install of maven download tar file in opt and extract and provide like 
	                                        //https://dlcdn.apache.org/maven/maven-3/3.8.4/binaries/apache-maven-3.8.4-bin.tar.gz
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
                sh "mvn clean install"      
				//sh "mvn clean //sh //mvn clean install -f mywebapp/prox.xml"   If pom.xml not in root folder
            }
        }
        //stage (sonarqubeanalysis) {
            //steps {
              //withSonarQubeEnv(credentialsId: 'sonarqube-cred', installationName: 'sonarqube-9') {      // You can override the credential to be used
	          //sh 'mvn sonar:sonar'                                                                        //sh "mvn sonar:sonar -f mywebapp/prox.xml"   If pom.xml not in root folder
               //sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
              //}
        //} 

        //stage (nexus_upload) {
           //steps {
              //nexusArtifactUploader artifacts: [[artifactId: 'maven-project', classifier: '', file: //'server/target/server.jar', type: 'pom']], credentialsId: 'nexus-cred', groupId: 'com.example.maven-project', //nexusUrl: '3.92.207.138:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'mvn-snapshot', version: //'1.0-SNAPSHOT'		
              //}
        //} 
		
        //stage (deploy_to_dev) {                         #tomcat
           //steps {
              //deploy adapters: [tomcat8(path: '', url: 'http://54.82.235.95:8080/')], contextPath: null, war: '**/*.jar'	
              //}
        //}
	
       // stage (slack notification) {
           //   steps {
           //     slackSend channel: 'dev', message: 'Deployment is done'
           //    }
          // } 
        stage ('DEV Approve') {
          steps {
            mail to: 'vinodkumar.chenna@gmail.com, chvinodgcp501@gmail.com', cc: 'vinodkumarchenna.gspann@gmail.com,chvinodgcp501@gmail.com', subject: "Please approve production deployment for aperture.gspann.com #${env.BUILD_NUMBER}", 
             body: """
               Hi,
                Please approve below feature for production release.
                 Sn.	Jira			Description
                 1	google         release of 2022
                Please click to approve the release in production : ${BUILD_URL}input/
                """
                input submitterParameter: 'userId', message: 'Ready?'
		}
           }
        //stage (deploy_to_QA) {                         #tomcat
           //steps {
              //deploy adapters: [tomcat8(path: '', url: 'http://54.82.235.95:8080/')], contextPath: null, war: '**/*.jar'	
              //}
        //}
	// stage (slack notification) {
          //   steps {
          //     slackSend channel: 'dev', message: 'Deployment is done'
          //    }
          // } 
     }				 
    post {
	  always {
		mail bcc: '', body: "<br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "${currentBuild.result} CI: Project name -> ${env.JOB_NAME}", to: "vinodkumar.chenna@gmail.com";  
		   }
	 }
  }

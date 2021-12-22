pipeline {
    agent any
    
    stages {
        stage (clone) {
            steps {
                git credentialsId: 'git-cred', url: 'https://github.com/vinodkumar501/hello-world.git'
		//checkout([$class: 'GitSCM', branches: [[name: 'refs/heads/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-cred', url: 'https://github.com/vinodkumar501/VND-ITRACK-JENKINSFILE-CICD-DEC2021.git']]])
            }
        }
        stage (test) {
            steps {
                echo "test"
            }
        }
        stage (deploy) {
            steps {
                echo "deploy"
           }
       }   
    }    
}

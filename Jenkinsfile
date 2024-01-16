pipeline{
    agent{
        label "jenkins-slave"
    }
    tools {
        jdk 'Java17'
        maven 'Maven3'
    }
    
    environment {
        APP_NAME= "devops-project"
        RELEASE = "1.0.0"
        DOCKER_USER = "nisahjalil1188"
        DOCKER_PASS = "dockerhub"
        IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
        IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
    }
    
    stages{
        stage("Cleanup Workspace"){
            steps {
                cleanWs()
            }

        }
    
        stage("Checkout from SCM"){
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/mehanisah/devops'
            }

        }
		
        stage("Build"){
            steps {
               sh "mvn clean package"
            }
        }
		
        stage("Test"){
            steps {
                sh "mvn test"
            }
        }

       
    }

}

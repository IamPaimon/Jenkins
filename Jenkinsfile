pipeline {
    agent any
    stages {
        stage ("Built maven") {
            steps{
                sh "pwd"
                sh "ls"
                sh "mvn clean install package"
            }
        }
         stage ('Copy Artifacts') {
            steps {
                sh "pwd"
                sh "cp -r target/*.jar docker"
            }
        }  
         stage ("Unit Tests") {
            steps {
                sh "mvn test"
            }
        } 
         stage('Build Docker Image'){
            steps{
                script {
                    def customImage = docker.build("iamsakib/petclinic:${env.BUILD_NUMBER}", "./docker")
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                    customImage.push()    
                }
            }
        }
    }

    }

}

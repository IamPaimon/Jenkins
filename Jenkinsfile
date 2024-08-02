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
           
    }

}

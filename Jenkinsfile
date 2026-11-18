
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
          
        stage('package') {
            steps {
                echo 'package running'
            }
        }

        stage('Deploy') { 
            steps {
                sh './jenkins/scripts/deploy.sh' 
            }
        }
    }
}

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
        }

        stage('Package') {
            steps {
                sh 'mvn package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    mkdir -p deploy
                    found=false
                    for artifact in target/*.war target/*.jar; do
                        [ -f "$artifact" ] || continue
                        cp "$artifact" deploy/
                        found=true
                    done
                    if [ "$found" = false ]; then
                        echo "No .war or .jar artifact found in target/"
                        exit 1
                    fi
                '''
            }
        }
    }
}

pipeline {
    agent any
    environment {
        DOCKER_CREDENTIALS_ID = 'dockerhub'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/ci-cd-optimization.git'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    docker.build('my-app:latest', '--cache-from=my-app:latest .')
                }
            }
        }

        stage('Push Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: "${DOCKER_CREDENTIALS_ID}", passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh '''
                        echo $PASS | docker login -u $USER --password-stdin
                        docker tag my-app:latest myusername/my-app:latest
                        docker push myusername/my-app:latest
                    '''
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'bash scripts/deploy.sh || bash scripts/rollback.sh'
            }
        }
    }
}

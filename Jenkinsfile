pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build("myapp:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'DockerHubCredentials') {
                        docker.image("myapp:${env.BUILD_NUMBER}").push()
                    }
                }
            }
        }
    }
}
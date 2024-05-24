pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/firaskhl/todo-devops.git'
            }
        }
        
        stage('Install Docker') {
            steps {
                script {
                    sh 'sudo apt update'
                    sh 'sudo usermod -aG docker $USER'
                    sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose'
                }
            }
        }
        stage('Docker Run') {
            steps {
                script {
                    sh 'sudo docker-compose up -d'
                    
                }
            }
        }
        stage('Puch docker image to docker ') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/',guesmihazem) {
                        docker.image("jenkins/jenkins:lts}").push()
                    }
                }
            }
        }
        stage('Deploy') {
    steps {
        script {
            sh 'kubectl apply -f deployment.yaml'
        }
    }
}
    }
}
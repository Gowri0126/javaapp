pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Gowri0126/javaapp.git'
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t javaapp:1.0 .'
            }
        }

        stage('Deploy to Docker Swarm') {
            steps {
                sh '''
                docker service rm javaapp_service || true
                docker service create \
                  --name javaapp_service \
                  javaapp:1.0
                '''
            }
        }
    }

    
    }


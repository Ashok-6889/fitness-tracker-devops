pipeline {
    agent any

    tools {
        jdk 'jdk17'
        maven 'maven'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Ashok-6889/fitness-tracker-devops.git'
            }
        }

        stage('Build') {
            steps {
                dir('backend/auth-service') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Docker Build') {
            steps {
                dir('backend/auth-service') {
                    sh 'docker build -t auth-service .'
                }
            }
        }

        stage('Docker Tag') {
            steps {
                sh 'docker tag auth-service ashok6889/auth-service:latest'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push ashok6889/auth-service:latest'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f auth-container || true'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker run -d -p 8081:8080 --name auth-container auth-service'
            }
        }
    }
}

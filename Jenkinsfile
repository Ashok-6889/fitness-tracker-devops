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
                    sh 'pwd'
                    sh 'ls -l'
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

        stage('Docker Run') {
            steps {
                sh 'docker run -d -p 8080:8080 auth-service'
            }
        }
    }
}

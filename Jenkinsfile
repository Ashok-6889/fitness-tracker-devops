pipeline {
    agent any

    tools {
        maven 'maven'
        jdk 'jdk17'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Ashok-6889/fitness-tracker-devops.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t fitness-app .'
            }
        }
    }
}

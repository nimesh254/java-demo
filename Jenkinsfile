pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean compile'
            }
        }

        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }

        stage('Package') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                sh './mvnw deploy -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t java-spring-calendar:latest .'
            }
        }
    }
}
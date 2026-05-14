pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-21-openjdk'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
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
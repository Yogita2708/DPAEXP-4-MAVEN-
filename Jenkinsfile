pipeline {
    agent any

    tools {
        // Ensure 'Maven 3' is configured in Jenkins Global Tool Configuration
        maven 'Maven 3' 
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

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
    }

    post {
        always {
            // Archive JUnit test results
            junit '**/target/surefire-reports/*.xml'
            // Archive the JAR/WAR file
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
        }
    }
}

pipeline {
    agent any

    tools {
        maven 'Maven-3.9.11'
    }

    stages {
        stage('Build main branch') {
            steps {
                git branch: 'main', url: 'https://github.com/Yogita2708/DPAEXP-4-MAVEN-.git'
                bat 'mvn clean package'
                bat 'ren target\\*.jar main-build.jar'
                archiveArtifacts artifacts: 'target/main-build.jar', fingerprint: true
            }
        }

        stage('Build master branch') {
            steps {
                git branch: 'master', url: 'https://github.com/Yogita2708/DPAEXP-4-MAVEN-.git'
                bat 'mvn clean package'
                bat 'ren target\\*.jar master-build.jar'
                archiveArtifacts artifacts: 'target/master-build.jar', fingerprint: true
            }
        }
    }
}

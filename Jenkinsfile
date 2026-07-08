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
                dir('calculator-app') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'calculator-app/target/*.jar', fingerprint: true
            }
        }
    }
}
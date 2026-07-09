pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                dir('calculator-app') {
                    sh 'mvn clean test package'
                }
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'calculator-app/target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            junit 'calculator-app/target/surefire-reports/*.xml'
        }
    }
}
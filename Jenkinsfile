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
                    sh 'mvn clean verify'
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

            jacoco(
                execPattern: 'calculator-app/target/jacoco.exec',
                classPattern: 'calculator-app/target/classes',
                sourcePattern: 'calculator-app/src/main/java'
            )
        }
    }
}
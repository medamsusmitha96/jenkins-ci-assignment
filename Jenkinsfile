pipeline {
    agent any

    tools {
        maven 'Maven_3.9.11' // Make sure this matches the Maven version installed in Jenkins
    }

    environment {
        // You can define environment variables here if needed
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/medamsusmitha96/jenkins-ci-assignment.git' // Replace with your actual repo URL
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed. Check the logs for details.'
        }
    }
}

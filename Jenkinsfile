pipeline {
    agent any

    tools {
        maven 'Maven_3.9.11'
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

   post {
    always {
        junit 'target/surefire-reports/*.xml'
    }
}

}

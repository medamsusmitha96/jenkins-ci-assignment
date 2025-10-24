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
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
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
        script {
            def reports = findFiles(glob: 'target/surefire-reports/*.xml')
            if (reports.length > 0) {
                junit 'target/surefire-reports/*.xml'
            } else {
                echo 'No test reports found to archive.'
            }
        }
    }
}

}

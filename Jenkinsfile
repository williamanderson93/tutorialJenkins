pipeline {
    agent any
    parameters {
        booleanParam(name: 'Refresh',
                    defaultValue: false,
                    description: 'Read Jenkinsfile and exit.')
                    }
    stages {
        stage('Update Apt Cache') {
            steps {
                sh 'sudo apt update'
            }
        }
        stage('Install Apache') {
            steps {
               sh 'sudo apt install apache2 -y'
            }
        }
    }
}
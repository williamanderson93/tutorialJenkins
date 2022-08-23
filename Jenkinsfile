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
                sudo apt update
            }
        }
        stage('Install Apache') {
            steps {
                sudo apt install apache2 -y
            }
        }
    }
}
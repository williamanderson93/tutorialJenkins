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
        stage('Edit File Permissions'){
            steps {
                sh 'sudo chown jenkins /var/www/html/index.html'
            }
        }
        stage('Edit File'){
            steps {
                sh 'echo "<h1>Hello from $(curl ifconfig.me)</h1>" > /var/www/html/index.html'
            }
        }
    }
}
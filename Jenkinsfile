pipeline {
    agent any
    parameters {
        booleanParam(name: 'Refresh',
                    defaultValue: false,
                    description: 'Read Jenkinsfile and exit.')
            }
    stages {
        stage('prune') {
            steps {
                sh 'sudo docker system prune -a -f'
            }
        }
        stage('build') {
            steps {
                sh 'sudo docker-compose build'
            }
        }
    }
}

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
        stage('test') {
            steps {
                sh 'python3 -m pytest ./prime/tests/test_unit.py'
            }
        }
        stage('build') {
            steps {
                sh 'sudo docker-compose build'
            }
        }
    }
}

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
        stage('Unit Tests') {
            steps {
                sh '''
                      python3 -m pytest ./converter/tests/test_unit.py
                      python3 -m pytest ./prime/tests/test_unit.py
                   '''
            }
        }
        stage('Integration Test') {
            steps {
                sh 'python3 -m pytest ./main/tests/test_unit.py'
            }
        }
    }
}

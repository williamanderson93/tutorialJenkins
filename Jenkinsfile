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
        stage('Deploy') {
            steps {
                sh '''
                #!bin/bash
                sudo ssh -i /home/jenkins/lamptestbox -o StrictHostKeyChecking=no ubuntu@18.133.242.2 << EOF
                rm -rf tutorialJenkins
                git clone https://github.com/williamanderson93/tutorialJenkins.git
                cd tutorialJenkins
                sudo docker-compose down
                sudo docker system prune -a -f
                sudo docker-compose up --build -d
                exit 0
                << EOF
            '''
            }
        }
    }
}
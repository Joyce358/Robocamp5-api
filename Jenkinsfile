pipeline {
    agent {
        docker{
            image 'python:3.7.7-stretch'
            args '--network=skynet'
        }
    }

    stages {
        stage('Build') {
            steps {
            sh 'pip install -r requirements.txt'
            }
        }
        stage('Testing') {
            steps {
                sh 'robot -d ./logs tests/'
            }
            post {
                always{
                robot 'logs'
                }
            }
        }
        stage('Aceite do usuário') {
            steps {
                echo 'Simulando a aprovação do PO'
                input(message: 'Voce aprova essa versão?', ok: 'Sim :)')
            }
        }
    }
}

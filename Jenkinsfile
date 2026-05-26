pipeline {

    agent any

    stages {

        stage('Clonar Projeto') {
            steps {
                echo 'Obtendo projeto do GitHub/GitLab...'
            }
        }

        stage('Diagnostico Docker') {
            steps {
                sh 'whoami'
                sh 'pwd'
                sh 'echo $PATH'
                sh 'which docker'
                sh 'docker --version'
            }
}

        stage('Build Docker') {
            steps {
                sh 'docker build -t pethero .'
            }
        }

        stage('Testar Container') {
            steps {
                sh 'docker rm -f pethero-test || true'
                sh 'docker run -d -p 8080:80 --name pethero-test pethero'
            }
        }

        stage('Verificar Container') {
            steps {
                sh 'docker ps'
            }
        }

    }

}
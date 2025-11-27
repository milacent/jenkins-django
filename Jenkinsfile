pipeline {
    agent any
    stages {
        stage('install requirements') {
            steps {
                sh 'pip3 install --break-system-packages -r requirements.txt'
            }
        }
        stage('tests') {
            steps {
                sh 'python3 manage.py test --verbosity=2'
            }
        }
        stage('hello') {
            steps {
                echo 'Hello world!'
            }
        }
    }
}

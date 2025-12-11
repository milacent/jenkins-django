pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'docker build -t django-demo .'
            }
        }
        stage('tests') {
            steps {
                sh 'docker run --rm django-demo python -m coverage run --source=. manage.py test --verbosity=2'
            }
        }
        stage('deploy') {
            steps {
                sh 'docker run -d --name django-demo -p 8001:8001 django-demo'
            }
        }
    }
}

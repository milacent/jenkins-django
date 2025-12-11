pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'docker build -t django-app .'
            }
        }
        stage('tests') {
            steps {
                sh 'docker run --rm django-app python -m coverage run --source=. manage.py test --verbosity=2'
            }
        }
        stage('deploy') {
            steps {
                sh 'docker run -d --name django-app -p 8001:8001 django-app'
            }
        }
    }
}

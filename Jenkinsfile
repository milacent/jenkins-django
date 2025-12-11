pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'docker build -t django-test-app .'
            }
        }
        stage('tests') {
            steps {
                sh 'docker run --rm django-test-app python -m coverage run --source=. manage.py test --verbosity=2'
            }
        }
        stage('deploy') {
            steps {
        	sh 'docker rm -f django-test-app || true'
                sh 'docker run -d --name django-test-app -p 8001:8001 django-test-app'
            }
        }
    }
}

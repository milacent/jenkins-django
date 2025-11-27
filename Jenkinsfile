pipeline {
    agent any
    
    stages {
        stage('req') {
            steps {
                git 'https://github.com/milacent/jenkins-django.git'
                sh 'pip3 install -r requirements.txt coverage'
            }
        }
        
        stage('coverage tests') {
            steps {
                sh '''
                    coverage run --source='.' manage.py test --verbosity=2
                    coverage report
                '''
            }
        }
    }
}
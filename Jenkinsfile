pipeline {
    agent any
    stages {
        stage('install requirements') {
            steps {
                sh 'pip3 install --break-system-packages -r requirements.txt'
		sh 'pip3 install --break-system-packages coverage'
            }
        }
        stage('tests') {
            steps {
                sh 'python3 manage.py test --verbosity=2'
		sh 'coverage report'
                sh 'coverage html'
            }
        }
	stage('artifacts') {
            steps {
                archiveArtifacts artifacts: 'htmlcov/**'
            }
        }
        stage('hello') {
            steps {
                echo 'Hello world!'
            }
        }
    }
}
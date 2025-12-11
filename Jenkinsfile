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
			sh "python3 -m coverage run --source='.' manage.py test --verbosity=2"
			sh 'python3 -m coverage report'
			sh 'python3 -m coverage html'
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
	stage('migrate') {
            steps {
                sh 'python3 manage.py makemigrations'
                sh 'python3 manage.py migrate'
            }
        }
        stage('run app') {
            steps {
                sh '''
		    python3 manage.py migrate
                    python3 manage.py runserver 0.0.0.0:8001
                '''
            }
        }
    }
}
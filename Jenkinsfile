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
    }
}
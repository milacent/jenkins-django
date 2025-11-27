pipeline {
    agent any
    
    stages { 
	stage('requirements') {
	    steps {
	        sh '''
		  python3 -m venv venv
		  . venv/bin/activate
		  pip install -r requirements.txt coverage django
		'''
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
	stage("hello") {
            steps {
                echo "Hello world!"
            }
        }
    }
}
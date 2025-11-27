pipeline {
    agent any
    stages { 
	stage('requirements') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }
        stage('tests') {
            steps {
                sh '''
                    python3 manage.py test --verbosity=2
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

pipeline {
    agent any
    stages { 
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

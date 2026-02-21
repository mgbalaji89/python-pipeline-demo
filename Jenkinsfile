pipeline {
    agent any 

    stages {
        stage('Check Environment') {
            steps {
                // Verify Python is installed on the host
                sh 'python3 --version'
            }
        }
        stage('Run Python') {
            steps {
                // Execute the script directly using the host's Python
                sh '''
                    python3 hello.py
                '''
            }
        }
    }
}

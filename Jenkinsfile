pipeline {
    agent {
        docker {
            image 'python:3.12'
            args '-u root'
        }
    }

    stages {

        stage('Install Dependencies') {
            steps {
                sh '''
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    pytest \
                    --junitxml=report.xml \
                    --html=report.html \
                    --self-contained-html
                '''
            }
        }
    }

    post {
        always {
            junit 'report.xml'

            publishHTML([
                allowMissing: false,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: '.',
                reportFiles: 'report.html',
                reportName: 'PyTest HTML Report'
            ])
        }
    }
}

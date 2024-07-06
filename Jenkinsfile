pipeline {
    agent any

    tools {
        nodejs 'Node 18'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Set up environment') {
            steps {
                configFileProvider([configFile(fileId: '.env', targetLocation: '.env')]) {
                    sh 'cat .env'  // This is just to verify the file content, you can remove it in production
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}

pipeline {
    agent any
    
    environment {
        ENV_FILE = credentials('001')
    }
    
    triggers {
        githubPush()
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Setup Environment') {
            steps {
                sh 'cp $ENV_FILE .env'
            }
        }
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        // Add additional stages as needed
    }
    
    post {
        success {
            cleanWs()
        }
    }
}

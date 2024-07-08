pipeline {
    agent any

    tools {
        // Install Node.js from the tool configuration
        nodejs 'nodejs-14' // Replace 'nodejs-14' with your configured Node.js version
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the repository
                git 'https://github.com/Vibhu0555/AwesomeProject.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install project dependencies
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // Run build command
                sh 'npm run build' // Adjust this if your build script is different
            }
        }

        stage('Test') {
            steps {
                // Run tests
                sh 'npm test'
            }
        }

        stage('Archive') {
            steps {
                // Archive artifacts, if needed
                archiveArtifacts artifacts: '**/build/**', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            // Actions to perform after every build
            junit '**/test-results/*.xml' // Publish test results if applicable
        }
    }
}

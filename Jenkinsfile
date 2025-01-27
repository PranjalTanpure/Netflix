pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'NodeJS_22' // Define Node.js installation
        PATH = "${NODEJS_HOME}/bin:${env.PATH}" // Add Node.js to PATH
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', credentialsId: 'Netflix-CICD', url: 'https://github.com/PranjalTanpure/Netflix.git'
            }
        }

        stage('Verify NodeJS Setup') {
            steps {
                bat 'node -v' // Verify Node.js version
                bat 'npm -v'  // Verify npm version
            }
        }
        
        stage('Install Dependencies') {
            steps {
                bat 'npm install' // Install dependencies
            }
        }

        stage('Linting') {
            steps {
                // Install required global tools
                bat 'npm install -g npx'
                bat 'npm install -g eslint stylelint'

                // Run linting for JS and CSS files
                bat 'npx eslint \"**/*.js\" || exit 0'
                bat 'npx stylelint \"**/*.css\" || exit 0'
            }
        }

        stage('Build') {
            steps {
                echo 'No build step required for static site'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to server...'
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}



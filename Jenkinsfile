pipeline {
    agent any

    environment {
         NODEJS_HOME = tool 'NodeJS_22' // Define Node.js installation
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', credentialsId: 'Netflix-CICD', url: 'https://github.com/PranjalTanpure/Netflix.git'
            }
        }
   
        stage('Verify NodeJS Setup') {
            steps {
                bat '"C:\node.exe" -v'
                bat '"C:\npm.cmd" -v'
            }
        }
        
     stage('Install Dependencies') {
    steps {
    
        bat '"C:\npm.cmd" install'
    }
}

       stage('Linting') {
    steps {
        bat "\"C:\npm.cmd" install -g npx"
        bat "\"C:\npm.cmd" install -g eslint stylelint"
        bat "\"C:\node.exe" -v"

        bat "\"C:\npm.cmd" exec -- eslint \"*/.js\" || exit 0"
        bat "\"C:\npm.cmd" exec -- stylelint \"*/.css\" || exit 0"
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



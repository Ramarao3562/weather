pipeline {
    agent any
    
    environment {
        API_KEY = credentials('a2975357b8d6f61b5d4f2793a549c5fa')  // store API key in Jenkins credentials
        NODE_ENV = 'production'
    }
    
    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/Ramarao3562/weather-app.git', branch: 'main'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                script {
                    // Install project dependencies
                    sh 'npm install'
                }
            }
        }
        
        stage('Build Application') {
            steps {
                script {
                    // Run the build command for production
                    sh 'npm run build'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    // Deploy to a specific server, directory, or S3 bucket
                    // Example: Copying build files to a deployment directory
                    sh 'cp -r build/* /path/to/your/deployment/directory'
                }
            }
        }
    }
    
    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed'
        }
    }
}

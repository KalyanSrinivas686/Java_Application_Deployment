pipeline {
    agent any

    environment {
        MAVEN_HOME = '/opt/maven' // Adjust this if Maven is installed in a different directory
        PATH = "${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git 'https://github.com/yourusername/Java_Application_Deployment.git'
            }
        }

        stage('Build') {
            steps {
                // Compile and package the Java application using Maven
                script {
                    if (fileExists('pom.xml')) {
                        sh 'mvn clean install'
                    } else {
                        error 'pom.xml not found!'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                script {
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy to the desired environment
                // Example: Deploy to a test server
                echo 'Deploying to Test Server...'

                // Deploy steps (e.g., using ssh, FTP, or other tools)
                // Example: sh 'scp target/myapp.war user@server:/path/to/deploy'
            }
        }

        stage('Post-deploy') {
            steps {
                // Example: notify Slack, send email, etc.
                echo 'Post-deployment actions'
            }
        }
    }

    post {
        success {
            echo 'Build and deploy successful!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}

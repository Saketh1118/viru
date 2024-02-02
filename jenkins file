pipeline {
    agent any
    
    environment {
        // Define any environment variables needed for the pipeline
        // For example:
        // MY_VARIABLE = 'some value'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                script {
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                // Build your application
                script {
                    // For example, if you are using Maven:
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                // Run tests for your application
                script {
                    // For example, if you are using JUnit:
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy') {
            when {
                // Define conditions when to deploy (e.g., only on the master branch)
                expression { 
                    return env.BRANCH_NAME == 'master'
                }
            }
            steps {
                // Deploy your application
                script {
                    // For example, deploy to a staging environment:
                    sh 'kubectl apply -f deployment.yaml'
                }
            }
        }
    }

    post {
        // Define post-build actions
        success {
            // Actions to be taken on successful build
        }
        failure {
            // Actions to be taken on build failure
        }
        unstable {
            // Actions to be taken when the build is unstable
        }
        changed {
            // Actions to be taken when the build status changes
        }
        fixed {
            // Actions to be taken when a broken build is fixed
        }
    }
}

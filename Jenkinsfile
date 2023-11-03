pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building the project"'
                // Add your build commands here
            }
        }

        stage('Test') {
            when {
                anyOf {
                    branch 'recette'
                    branch 'prod'
                }
            }
            steps {
                sh 'echo "Running tests"'
                // Add your test commands here
            }
        }

        stage('Deploy') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'dev') {
                        sh 'echo "Deploying to Dev environment"'
                        // Add deployment commands for Dev
                    } else if (env.BRANCH_NAME == 'recette') {
                        sh 'echo "Deploying to Recette environment"'
                        // Add deployment commands for Recette
                    } else if (env.BRANCH_NAME == 'prod') {
                        sh 'echo "Deploying to Production environment"'
                        // Add deployment commands for Production
                    } else {
                        sh 'echo "No specific deployment for this branch"'
                    }
                }
            }
        }
    }
}

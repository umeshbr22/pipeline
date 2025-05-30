pipeline {
    agent any

    parameters {
        string(name: 'ENVIRONMENT', defaultValue: 'dev', description: 'Target Environment')
        booleanParam(name: 'DO_DEPLOY', defaultValue: true, description: 'Should deploy after build?')
        choice(name: 'BRANCH', choices: ['main', 'develop', 'release'], description: 'Select Git branch')
    }

    stages {
        stage('Print Parameters') {
            steps {
                echo "Environment: ${params.ENVIRONMENT}"
                echo "Should Deploy: ${params.DO_DEPLOY}"
                echo "Selected Branch: ${params.BRANCH}"
            }
        }

        stage('Build') {
            when {
                expression { params.ENVIRONMENT == 'dev' }
            }
            steps {
                echo "Running build for DEV environment..."
            }
        }

        stage('Deploy') {
            when {
                expression { params.DO_DEPLOY == true }
            }
            steps {
                echo "Deploying to ${params.ENVIRONMENT} environment"
            }
        }
    }
}

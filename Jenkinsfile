pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['DEV', 'QA', 'PROD'], description: 'Select the environment')
        string(name: 'VERSION', defaultValue: '1.0', description: 'Enter the version number')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building version ${params.VERSION} for ${params.ENVIRONMENT} environment"
                // Add your build steps here
            }
        }

        stage('Test') {
            steps {
                echo "Running tests for version ${params.VERSION} in ${params.ENVIRONMENT} environment"
                // Add your test steps here
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${params.VERSION} to ${params.ENVIRONMENT} environment"
                // Add your deployment steps here
            }
        }
    }
}

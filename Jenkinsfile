pipeline {
    agent any
    parameters {
        string(name: 'APP_NAME', defaultValue: 'Netflix', description: 'This is for Netflix app')
        string(name: 'APP_VERSION', defaultValue: '1.0', description: 'This is for app version')
        choice(name: 'ENV', choices: ['dev', 'stage', 'prod'], description: 'Select the environment')
        booleanParam(name: 'IS_PROD', defaultValue: true, description: 'Is this production deployment?') 
    }
    environment {
        APP_ENV = "${params.APP_NAME}"
    }
    stages {
        stage('Info') {
            steps {
                echo "Application Name is ${params.APP_NAME}"
                echo "Application Version is ${params.APP_VERSION}"
                echo "Environment selected is ${params.ENV}"
                echo "Is production deployment? : ${params.IS_PROD}"
            }
        }
        stage('build') {
            steps {
                echo "Building ${params.APP_NAME}:${params.APP_VERSION}"
                sh 'echo Build step simulated'
            }
        }
        stage('test') {
            when {
                expression { params.IS_PROD }
            }
            steps {
                echo "Running tests for production deployment"
                sh 'echo Test step stimulated'
            }
        }
        stage('deploy') {
            steps {
                echo "Deploying ${params.APP_NAME}: ${params.APP_VERSION}"
                sh 'echo Deploy step stimulated'
            }
        }
    }
    post {
        success {
            echo "Pipeline completed successfully"
        }
        failure {
            echo "Pipeline failed"
        }
        always {
            echo "Pipeline finished (success or failure)"
        }
    }
}

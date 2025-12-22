pipeline {
    agent any
    environment {
        APP_ENV = "Netflix"
    }
    stages {
        stage ('build') {
            steps {
                echo "Building...!"
            }
        }
        stage ('test') {
            steps {
                echo " ${APP_ENV} app is running successfully!"
                echo " Build number is ${BUILD_NUMBER}"
                echo " Job name is ${JOB_NAME}"
                echo " Workspace path is ${WORKSPACE}"

            }
        }
    }
    post {
        success {
            echo "pipeline succeeded!"
        }
        failure {
            echo "pipeline failed! "
        }
    }
}

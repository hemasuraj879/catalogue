pipeline {
    agent { label 'agent' }

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/hemasuraj879/catalogue.git'
            }
        }
    }

    stages{
        stage('Test Purpose') {
            steps {
                echo 'testing will be done here'
            }
            
        }
    }

    post {
        success {
            echo 'Pipeline is successful!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
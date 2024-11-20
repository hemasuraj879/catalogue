pipeline {
    agent { label 'agent' }

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/hemasuraj879/catalogue.git'
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
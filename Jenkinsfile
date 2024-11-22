

pipeline {
    agent { label 'agent' }

    stages {
        stage('DOCKER LOGIN CHECK') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker-auth', usernameVariable: 'username', passwordVariable: 'password')]) {
                        sh """
                            docker login -u $username -p $password
                        """
                    }
                }
            }
        }

        stage('DOCKER IMAGE BUILD') {
            steps {
                sh """
                    docker build -t $username/$JOB_NAME:$BUILD_ID .
                """
            }
        }
    }
}
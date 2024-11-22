pipeline {
    agent { label 'agent' }

    stages {
        stage('DOCKER LOGIN CHECK') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker-auth', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        echo "Username is: $USERNAME"
                        sh """
                            docker login -u $USERNAME -p $PASSWORD
                        """
                    }
                }
            }
        }
        
        stage('DOCKER IMAGE BUILD'){
          steps {
            sh """
              docker $USERNAME/$JOB_NAME:$JOB_ID .
            """
          }
        }
    }
}
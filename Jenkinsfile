pipeline {

    agent { label 'agent'}

    stages{
        stage('DOCKER LOGIN CHECK'){
            steps{
                script{
                  withCredentials([usernamePassword(credentialsId: 'docker-auth', usernameVariable: 'username', passwordVariable: 'password')]){
                    sh """
                        docker login -u $username -p $password
                    """
                  }
                }
            }
        }
        stage('DOCKER IMAGE BUILD AND PUSH'){
            steps{
                sh """
                    docker build -t surajk879/$JOB_NAME:$BUILD_NUMBER .
                    docker push surajk879/$JOB_NAME:$BUILD_NUMBER
                """ 
            }
        }

        stage('DEPLOY TO EKS CLUSTER'){
            steps{
                sh """
                  sed -i 's/surajk879\/catalogue:1.9/surajk879\/$JOB_NAME:$BUILD_NUMBER/g' manifest.yaml
                  kubectl apply -f manifest.yaml
                  
                """
            }
        }
    }

    post{
        always{
            //cleaning up workidr
            deleteDir()
        }
        success{
              echo "$JOB_NAME IS SUCCESS"
        }
        failure{
              echo "$JOB_NAME IS FAILURE"
        }
    }
}
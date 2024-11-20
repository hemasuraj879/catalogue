pipeline {
  agent { label 'agent' }

  stages {
    stage('Git Checkout') {
      steps {
        git 'https://github.com/hemasuraj879/catalogue.git'
      }
    }
    stage('DOCKER IMAGE BUILD'){
        steps{
            sh """
                docker build -t surajk879/catalogue:1.11 .
            """
        }
    }

    stage('DOCKER IMAGE PUSH'){
        steps{
            sh  """
                docker push surajk879/catalogue:1.11
            """
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
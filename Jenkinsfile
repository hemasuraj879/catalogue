pipeline {
    agent { label 'agent' }

    stages{
        stage('Git Checkout'){
            steps{
                git 'https://github.com/hemasuraj879/catalogue.git'
            }

        }
        
    }
}

post {

    succss {
        echo  'pipeline is success'
    }

    failure {
        echo 'pipeline is failure'
    }
}
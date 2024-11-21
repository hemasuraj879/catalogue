pipeline {

  agent { label 'sonarqube' }

  stages {

    stage('GIT CHECKOUT'){
      steps{
        git 'https://github.com/hemasuraj879/catalogue.git'
      }
    }

    stage('INSTALL DEPENDENCIES'){
      steps{
        sh 'npm install'
      }
    }

    // Move "SONAR-SCAN" steps inside a stage definition
    stage('SONAR SCAN'){
      steps{
        sh 'sonar-scanner'
      }
    }
  }
}
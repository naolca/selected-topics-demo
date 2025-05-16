pipeline {
  agent any
  tools {
    sonarqubeScanner 'SonarQube Scanner'
  }
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/your-username/microservices-demo-nestjs.git'
      }
    }
    stage('Install & Test') {
      steps {
        sh 'npm install'
        sh 'npm run test -- --coverage'
      }
    }
    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('sonarqube') {
          sh 'sonar-scanner -Dsonar.projectKey=microservices-demo-nestjs-user-service'
        }
      }
    }
  }
}
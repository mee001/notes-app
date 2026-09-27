pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker compose -f docker-compose.prod.yml build notes-app'
      }
    }
    stage('Test Nginx') {
      steps {
        sh 'docker run --rm notes-app nginx -t'
      }
    }
    stage('Deploy') {
      steps {
        sh 'docker compose -f docker-compose.prod.yml up -d'
      }
    }
  }
}

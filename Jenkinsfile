pipeline {
  agent any

  stages {
    stage('Start WireMock') {
      steps {
        sh 'docker compose up -d'
        sh 'sleep 5'
      }
    }

    stage('Run Newman tests') {
      steps {
        sh 'newman run wiremock-movies-tests.postman_collection.json'
      }
    }

    stage('Stop WireMock') {
      steps {
        sh 'docker compose down'
      }
    }
  }
}
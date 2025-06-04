pipeline {
  agent any

  stages {
    stage('Start WireMock') {
      steps {
        bat 'docker compose up -d'
        bat 'timeout /t 5'
      }
    }

    stage('Run Newman tests') {
      steps {
        bat 'newman run wiremock-movies-tests.postman_collection.json'
      }
    }

    stage('Stop WireMock') {
      steps {
        bat 'docker compose down'
      }
    }
  }
}
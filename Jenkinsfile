pipeline {
  agent any

  stages {
    stage('Start WireMock') {
      steps {
        bat 'docker compose up -d'
        bat 'ping -n 6 127.0.0.1 >nul'
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
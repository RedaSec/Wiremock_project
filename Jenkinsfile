pipeline {
  agent any

  stages {
    stage('Start WireMock') {
      steps {
        echo 'Lancement de WireMock...'
        bat 'docker-compose up -d'
        bat 'ping -n 6 127.0.0.1 >nul'
      }
    }

    stage('Run Newman tests') {
      steps {
        echo 'Exécution des tests Postman avec Newman...'
        bat '"C:\\Users\\RedaDERRASSI\\AppData\\Roaming\\npm\\newman.cmd" run wiremock-movies-tests.postman_collection.json'
      }
    }

    stage('Stop WireMock') {
      steps {
        echo 'Arrêt de WireMock'
        bat 'docker-compose down'
      }
    }
  }
}
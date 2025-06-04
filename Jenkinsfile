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
        bat '"C:\\Users\\RedaDERRASSI\\AppData\\Roaming\\npm\\newman.cmd" run postman.json --reporters cli,html,json --reporter-html-export newman-report.html --reporter-json-export result.json'
      }
    }

    stage('Stop WireMock') {
      steps {
        echo 'Arrêt de WireMock'
        bat 'docker-compose down'
      }
    }
  }

  post {
    always {
      echo 'Archivage des rapports Newman...'
      archiveArtifacts artifacts: 'newman-report.html, result.json', fingerprint: true
    }
  }
}

pipeline {
  agent any
  stages {
    stage('Launch NeoLoad') {
      steps {
        timeout(time: 30) {
          bat(script: '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp"', returnStatus: true, returnStdout: true)
        }

      }
    }
    stage('Launch Selenium script') {
      steps {
        sleep 5
      }
    }
    stage('Kill NeoLoad') {
      steps {
        bat ' Taskkill /IM NeoLoadGUI_NoPrivilege.exe /F'
      }
    }
  }
}
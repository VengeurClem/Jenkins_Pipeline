pipeline {
  agent any
  stages {
    stage('Launch NeoLoad') {
      steps {
        bat 'cd "C:\\Users\\Clem\\Documents"'
        bat '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "PassionFroid.nlp"'
        sleep 10
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
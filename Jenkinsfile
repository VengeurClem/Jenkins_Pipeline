pipeline {
  agent any
  stages {
    stage('Launch NeoLoad') {
      steps {
        bat 'cd "C:\\Users\\Clem\\Documents"'
        bat '%neoload%\\NeoLoadGUI_NoPrivilege.exe -project "PassionFroid.nlp"'
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
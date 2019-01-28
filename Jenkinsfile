pipeline {
  agent any
  stages {
    stage('Launch NeoLoad') {
      steps {
        sh '''cd C:\\Program Files\\NeoLoad 6.8\\bin
 .\\NeoLoadGUI_NoPrivilege.exe -project "C:\\Users\\Clem\\Documents\\NeoLoad Projects\\PassionFroid\\Ne
oLoad\\PassionFroid.nlp"
'''
      }
    }
    stage('Launch Selenium script') {
      steps {
        sleep 5
      }
    }
    stage('Kill NeoLoad') {
      steps {
        sh ' Taskkill /IM NeoLoadGUI_NoPrivilege.exe'
      }
    }
  }
}
pipeline {
  agent any
  stages {
    stage('change script in neoload') {
      parallel {
        stage('change script in neoload') {
          steps {
            bat '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp"'
          }
        }
        stage('') {
          steps {
            sleep(unit: 'MINUTES', time: 5)
            bat 'taskkill /IM NeoLoadGUI_NoPrivilege.exe /F'
          }
        }
      }
    }
    stage('Launch test') {
      steps {
        bat '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp" -launch "scenario1"'
      }
    }
  }
}
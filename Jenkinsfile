pipeline {
  agent any
  stages {
    stage('change script in neoload') {
      parallel {
        stage('change script in neoload') {
          steps {
            catchError() {
              bat '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp"'
            }

          }
        }
        stage('error') {
          steps {
            sleep(unit: 'MINUTES', time: 4)
            bat 'taskkill /IM NeoLoadGUI_NoPrivilege.exe /F'
          }
        }
      }
    }
    stage('Launch test') {
      steps {
        catchError() {
          bat '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp" -launch "scenario1" - report "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\reports\\myReports.html" -exit'
        }

      }
    }
    stage('error') {
      steps {
        echo 'This is the end'
      }
    }
  }
}
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
        stage('See me I\'m your killer') {
          steps {
            sleep(unit: 'MINUTES', time: 2)
            bat 'java -jar "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\out\\artifacts\\PassionFroid_jar\\EpiSaveursSeleniumTestAutomation.jar"'
            bat 'taskkill /IM NeoLoadGUI_NoPrivilege.exe /F'
          }
        }
      }
    }
    stage('Launch test') {
      parallel {
        stage('Launch test') {
          steps {
            catchError() {
              bat '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp" -launch "scenario1" -report "C:\\Program Files (x86)\\Jenkins\\workspace\\Jenkins_Pipeline_master\\myReports.html" '
            }

          }
        }
        stage('I kill you') {
          steps {
            sleep(time: 6, unit: 'MINUTES')
            neoloadRefreshTrends(maxTrends: 1, showTrendAverageResponse: true, showTrendErrorRate: true)
            bat 'taskkill /IM NeoLoadGUI_NoPrivilege.exe /F'
          }
        }
      }
    }
    stage('Message') {
      steps {
        echo 'This is the end'
      }
    }
  }
}
pipeline {
  agent any
  stages {
    stage('Launch NeoLoad') {
      steps {
        timeout(time: 30) {
          bat(script: '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp"', returnStatus: true)
        }

      }
    }
    stage('Launch Selenium script') {
      steps {
        sleep 20
      }
    }
    stage('Kill NeoLoad') {
      steps {
        bat ' Taskkill /IM NeoLoadGUI_NoPrivilege.exe /F'
      }
    }
    stage('Launch test') {
      steps {
        neoloadRun executable: 'C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadCMD', scenario: 'scenario1', project: 'C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp', trendGraphs: ['AvgResponseTime', 'ErrorRate']
      }
    }
  }
}

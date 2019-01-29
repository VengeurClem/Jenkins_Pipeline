pipeline {
  agent any
  stages {
    stage('change script in neoload') {
      steps {
        bat(script: '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp"', returnStatus: true)
        sleep 20
        bat ' Taskkill /IM NeoLoadGUI_NoPrivilege.exe /F'
      }
    }
    stage('Launch test') {
      steps {
        neoloadRun(executable: 'C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadCMD', scenarioName: 'scenario1', projectType: 'C:\\Users\\Clem\\Documents\\NeoLoad_Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp')
      }
    }
  }
}
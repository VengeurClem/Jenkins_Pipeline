pipeline {
  agent any
  stages {
    stage('Launch NeoLoad') {
      steps {
        bat ' Taskkill /IM NeoLoadGUI_NoPrivilege.exe /F'
        bat '"C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI_NoPrivilege.exe" -project "C:\\Users\\Clem\\Documents\\NeoLoad Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp"'
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
    stage('Execute script') {
      steps {
        neoloadRun(scenarioName: 'Scenario1', executable: 'C:\\Program Files\\NeoLoad 6.8\\bin\\NeoLoadGUI.exe', localProjectFile: 'C:\\Users\\Clem\\Documents\\NeoLoad Projects\\PassionFroid\\NeoLoad\\PassionFroid.nlp', licenseType: 'C:\\Program Files\\NeoLoad 6.8\\bin\\FreeEditionLicense.lic')
      }
    }
  }
}
node {
   stage('Git checkout') { // for display purposes
      git 'https://github.com/princy1612/my_own1.git'
   }
   stage('Regression') {
        try {
            sh "mvn clean verify -Dtags='type:Regression'"
        } catch (err) {
            
        } finally {
            publishHTML (target: [
            reportDir: 'target/site/serenity',
            reportFiles: 'cucumber_report.html',
            reportName: " Regression tests report"
            ])
        }
   }
   stage('API') {
        try {
            sh "mvn clean verify -Dtags='type:API'"
        } catch (err) {

        } finally {
            publishHTML (target: [
                    reportDir: 'target/site/serenity',
                    reportFiles: 'cucmber_report.html',
                    reportName: "API tests report"
            ])
        }
    }
  
   stage('Results') {
      //junit '**/failsafe-reports/*.xml'
      //junit '**/report/*.xml'
      junit '**/target/failsafe-reports/*.xml'
   }
}

node {
   stage('Git checkout') { // for display purposes
      git 'https://github.com/princy1612/my_own1.git'
   }
   stage('Smoke') {
        try {
            sh "mvn clean verify -Dtags='type:Regression'"
        } catch (err) {
            
        } finally {
            publishHTML (target: [
            reportDir: 'target/report',
            reportFiles: 'cucumber_report.html',
            reportName: " Regression tests report"
            ])
        }
   }
  
   stage('Results') {
      junit '**/failsafe-reports/*.xml'
   }
}

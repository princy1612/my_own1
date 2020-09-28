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
   stage('API') {
        try {
            sh "mvn clean verify -Dtags='type:API'"
        } catch (err) {
            
        } finally {
            publishHTML (target: [
            reportDir: 'target/site/serenity',
            reportFiles: 'cucumber_report.html',
            reportName: "API tests report"
            ])
        }
   }
   stage('UI') {
        try {
            sh "mvn verify -Dtags='type:UI'"
        } catch (err) {
            
        } finally {
            publishHTML (target: [
            reportDir: 'target/site/serenity',
            reportFiles: 'cucumber_report.html',
            reportName: "UI tests report"
            ])
        }
   }
   stage('Results') {
      junit '**/target/reports/*.xml'
   }
}

node {
   stage('Git checkout') { // for display purposes
      git 'https://github.com/princy1612/git__html.git'
   }
   stage('Smoke') {
        try {
            sh "mvn clean verify -Dtags='type:Smoke'"
        } catch (err) {
            
        } finally {
            publishHTML (target: [
            reportDir: 'target/site/serenity',
            reportFiles: 'index.html',
            reportName: "Smoke tests report"
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
            reportFiles: 'index.html',
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
            reportFiles: 'index.html',
            reportName: "UI tests report"
            ])
        }
   }
   stage('Results') {
      junit '**/target/failsafe-reports/*.xml'
   }
}

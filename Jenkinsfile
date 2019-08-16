node {
   
   stage('Preparation') { 
      git 'https://github.com/vuppalapati/fleetman-webapp'
     
   }
   stage('Build') {
      sh "mvn package"
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
}

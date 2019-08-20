node {
   
   stage('Preparation') { 
      git 'https://github.com/vuppalapati/fleetman-webapp'
     
   }
   stage('Build') {
      sh "mvn clean package"
   }
   stage('Results') {
      archiveArtifacts 'target/*.war'
   }
   withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'awscredentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
      ansiblePlaybook credentialsId: 'ssh-credentials', installation: 'ansible-installation', playbook: 'deploy.yaml'
}

pipeline {

   agent {
        label 'jenkins-agent'
   }

   triggers {
      pollSCM '* * * * * '
   }

   stages {
   
      stage ('scm-checkout') {
         steps {
            checkout scmGit(branches: [[name: '*/feat01']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-creds-jyothika', url: 'https://github.com/whatsapp-jyo/mavenrepo.git']])
            sh ' echo "my first pipeline" '
          }

      }
      
      stage ('mvn build') {
          steps{
              sh ' mvn package '
            }

      }

   }         //all stages complete here

}            //pipeline completes here

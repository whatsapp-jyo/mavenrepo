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
      }         //scm stage completes here
      
      stage ('mvn build') {
          steps{
              sh ' mvn package '
            }
      }       //build stage completes here

      stage ('code quality') {
          steps{
              sh ' mvn sonar:sonar '
            }
      }       //sonar stage completes here

      stage ('upload artifact') {
          steps{
              sh ' mvn deploy '
            }
      }       //artifact upload to nexus repo stage completes here

      stage ('deploy artifact ') {
          steps{
              sh ' scp /root/workspace/whattsapp/chatting/build/sample-dev/target/studentapp-2.1.1-FEAT01-SNAPSHOT.war root@172.31.1.252:/opt/apache-tomcat-10.0.23/webapps '
            }
      }       //install artifact on Tomcat 
      

   }         //all stages complete here

}            //pipeline completes here

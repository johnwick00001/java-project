pipeline{
     agent any
     tools{
        maven 'local_maven'
       }
      stages{
          stage ('Build'){
             steps{
                 sh 'mvn clean package'
              }
             post{
                 success{
                         echo "Archiving the Artifacts"
                       archiveArtifacts artifacts: '**/target/*.war'
                         }
                    }
               }
             stage ('Deploy to tomcat server') {
             steps{
             deploy adapters: [tomcat9(credentialsId: 'caed19db-1d6b-4885-9029-c92a52278191', path: '', url: 'http://54.210.233.72:8080/')], contextPath: null, war: '**/*.war'
            }
        }
   }
}





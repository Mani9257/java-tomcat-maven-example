
          node {
                    stage("build & SonarQube analysis") {
              //withSonarQubeEnv('My SonarQube Server') {
                 // sh 'mvn clean package sonar:sonar'
                 sh '/opt/apache-maven-3.6.3/bin/mvn clean package sonar:sonar'
              }    
          }
      }
      
      stage("Quality Gate"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
      }        

 

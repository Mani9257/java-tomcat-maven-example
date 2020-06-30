pipeline {
        agent none
        stages {
          stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('sonarqube') {
                sh '/opt/apache-maven-3.6.3/bin/mvn clean package sonar:sonar'
              }
            }
          }
          stage("Quality Gate") {
            steps {
              timeout(time: 30, unit: 'SECONDS') {
                def qg = waitForQualityGate() 

              if (qg.status != 'OK') { 

                  error "Pipeline aborted due to quality gate failure: ${qg.status}" 

              } 
              }
            }
          }
        }
      }

 

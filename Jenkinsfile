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
              timeout(time: 2, unit: 'minutes') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
        }
      }

 

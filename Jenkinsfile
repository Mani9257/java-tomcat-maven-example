node('master'){ 

    stage('git checkout'){ 

                  git 'https://github.com/Mani9257/java-tomcat-maven-example.git' 

              } 

   stage('java build'){ 

             sh '/opt/apache-maven-3.6.3/bin/mvn clean deploy sonar:sonar -Dsonar.password=admin -Dsonar.login=admin' 

         } 

    stage("build & SonarQube analysis") { 

              withSonarQubeEnv(‘sonar') { 

                 sh '/opt/apache-maven-3.6.3/bin/mvn clean package sonar:sonar' 

              } 

          } 

      stage("Quality Gate"){ 

          timeout(time: 30, unit: 'SECONDS') { 

              def qg = waitForQualityGate() 

              if (qg.status != 'OK') { 

                  error "Pipeline aborted due to quality gate failure: ${qg.status}" 

              } 

          } 

      }  
 } 

 

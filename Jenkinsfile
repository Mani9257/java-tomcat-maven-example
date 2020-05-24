node{
       
      stage('Checkout'){
         git 'https://github.com/Mani9257/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
            /// def mvnHome = tool name: 'MAVEN-HOME', type: 'maven'
       sh label: '', script: 'C:\\apache-maven-3.6.2\\bin\\mvn clean install '
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') {     
            sshagent(['Tomcat-jenkins']) {
               sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war jenkins@35.193.54.220:/opt/tomcat/webapps'
              
          }
         
     }
      
 }

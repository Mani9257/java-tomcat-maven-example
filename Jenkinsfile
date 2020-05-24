node{
      def mvnHome = tool name: 'MAVEN-HOME', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/Mani9257/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
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

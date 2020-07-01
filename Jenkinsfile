
          node{
   stage('SCM Checkout'){
     git 'https://github.com/Mani9257/java-tomcat-maven-example.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'M2_HOME', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   
   stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'M2_HOME', type: 'maven'
        withSonarQubeEnv('sonarqube') { 
          sh "${mvnHome}/bin/mvn sonar:sonar"
        }
    }
    
    stage("Quality Gate Status Check"){
          timeout(time: 30, unit: 'SECONDS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') 
                   // slackSend baseUrl: 'https://hooks.slack.com/services/',
                    //channel: '#jenkins-pipeline-demo',
                    // color: 'danger', 
                   // message: 'SonarQube Analysis Failed', 
                    // teamDomain: 'javahomecloud',
                   // tokenCredentialId: 'slack-demo'
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              
          }
      }    
}


 

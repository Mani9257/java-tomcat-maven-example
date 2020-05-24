pipeline
{
       agent any
       
       stages{
              stage("git"){
                     steps{
                            git 'https://github.com/Mani9257/java-tomcat-maven-example'
                     }
              }
              stage("build"){
                     
                     steps{
                            
                            bat "${mvnHome}\\bin\\mvn clean install"
                     }
              }
       }
}
    
                            
       

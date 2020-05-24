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
                            
                            bat "C:\\apache-maven-3.6.2\\bin\\mvn clean install"
                     }
              }
       }
}
    
                            
       

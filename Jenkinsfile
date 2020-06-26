node{
   
   stage('SCM Checkout'){
     git 'https://github.com/Nirmalraaj/test2'
   }
   stage('Compile-Package'){
      // Get maven home path
    def mvn_home = 'maven'
    withEnv( ["PATH+MAVEN=${tool mvn_home}/bin"] ) {
     sh "mvn clean install"
    }
   }
   stage('Deploy to Tomcat'){
    sshagent(['jenkins_tom']) {
    sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pipeline_test2/target/*.war  ec2-user@100.25.196.81:/home/ec2-user/tomcat7/webapps/'
     }
    
    }
   stage ("build another job") {		
         
                build 'delivery_line_1'	
            
        }
  
}
   
 

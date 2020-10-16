  node{
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
 
   }
stage('Deploy to tomcat'){
  sshagent(['tomcat-deployment']) {
      sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.84.153:/opt/tomcat8/webapps/'
  }
}
  




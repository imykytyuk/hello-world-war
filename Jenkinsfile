node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/imykytyuk/hello-world-war.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'maven-3.6.0'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" clean package/)
      }
   }
   stage('Deploy') {
      sh 'scp ${JENKINS_HOME}/workspace/${JOB_NAME}/target/hello-world-war-1.0.0.war tomcat8@172.31.14.160:/usr/tomcat8/webapps/'
      
   }
}


pipeline {
  agent { label 'label1' }
  stages {
    stage ('CLONE') {
      steps {
        echo "cloning java project from git"
        sh ''' 
		git pull https://github.com/cpdani14/Test1_Java.git
	   '''
        }
    }
   stage ('BUILD') {
		agent { label 'label1' }
		steps {
			echo "Build a binary"
        sh ''' 
			mvn clean package
	   '''
      }
    }
	stage ('DEPLOY') {
                steps {
                    script{
			    
			    sudo cp /opt/jenkins/workspace/Test1_Java/target/hello-world-war-1.0.0.war  /opt/tomcat/webapps/
                    
		    }
                }
 	 }
	 stage ('TEST') {
		steps {
			echo "Testing the build"
        sh ''' 
			sleep 5
	   '''
      }
    }
  }
}  

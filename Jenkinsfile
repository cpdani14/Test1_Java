pipeline {
  agent { label 'label1' }
  stages {
    stage ('CLONE') {
      steps {
        echo "cloning java project from git"
        sh ''' 
		    git clone https://github.com/cpdani14/test2_java.git
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
                    deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://43.204.36.139:8080/')], contextPath: 'deploy-to-tomcat', war: '*/.war'
                    deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://43.204.36.139:8080/')], contextPath: null, war: '**/*.war'
		    }
                }
 	 }
  }
}  

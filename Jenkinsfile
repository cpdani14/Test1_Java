pipeline{
    agent{
        label 'label1'
    }
    stages{
        stage('CLONING REPO'){
            steps{
                git clone 'https://github.com/cpdani14/Test1_Java.git'
            }
        }    
            stage('BUILD'){
                steps{
                  sh 'mvn clean install'  
                }
            }
            stage('DEPLOYING'){
                steps{
                     echo "archiving"
                        archiveArtifacts artifacts: '*/*.war', followSymlinks: false
                }
                post{
                    success{
                        deploy adapters: [tomcat9(credentialsId: 'tomcat_cred_robot', path: '', url: 'http://43.204.36.139:8080/')], contextPath: null, war: '*/*.war'

                    }
                }
            }
    }
}

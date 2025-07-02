pipeline {
      agent any

      stages {
             stage("scm") {
	          steps { 
		         git branch: 'main', url: 'https://github.com/technet001/logindocker.git'
			 }
		      }
             stage("build") {
	          steps { 
		         sh 'sudo mvn clean package'
			 }
		      }
	     stage("build-image") { 
	          steps {
	                 sh 'sudo docker build -t tomcat-repo:$BUILD_TAG .'
			 sh 'sudo docker tag tomcat-repo:$BUILD_TAG technetgalaxy/docklogin'
                         } 
	              }
             stage("dockerlogin") {
	          steps {
		         withCredentials([string(credentialsId: 'login_pass', variable: 'login_var')]) {
                         sh 'sudo docker login -u technetgalaxy -p ${login_var}'
			 sh 'sudo docker push technetgalaxy/docklogin:$BUILD_TAG'
			 }
                       }
	          }
            }
}

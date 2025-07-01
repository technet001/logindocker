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
	                 sh 'sudo docker build -t tomcat-repo:$BUILD_TAG .'
			 sh 'sudo docker tag tomcat-repo:$BUILD_TAG technetgalaxy/docklogin'
             }
	 }
}

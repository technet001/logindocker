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
             }
}

pipeline {

	agent {
	    node {
	      label 'master'
	      customWorkspace '/root/test'
	    }
	  }

	tools {
    	maven 'apache-maven-3.9.9' 
	}

	environment {
        MAVEN_HOME = '/root/tools/apache-maven-3.9.9'  // Adjust as needed
        PATH = "${env.PATH}:${MAVEN_HOME}/bin"
    	}		

	stages {

		stage ('build') {
			steps {
				sh "mvn clean install"
			}
		}
		
		stage ('deploy') {
			steps {
				sh "sudo cp /root/test/target/LoginWebApp.war /root/servers/apache-tomcat-10.1.41/webapps/"
				sh "sudo chmod -R /root/servers/apache-tomcat-10.1.41/webapps/LoginWebApp.war"
			}
		}

		stage ('run') {
			steps {
				sh "sudo cd /root/servers/apache-tomcat-10.1.41/bin/"
				sh "./startup.sh"
			}
		}
	}
}

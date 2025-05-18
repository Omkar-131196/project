pipeline {

	agent {

		label 'master'
	}

	tools {
    	maven 'apache-maven-3.9.9' 
	}

	environment {
        MAVEN_HOME = '/root/tools/apache-maven-3.9.9'  // Adjust as needed
        PATH = "${env.PATH}:${MAVEN_HOME}/bin"
    	}		

	stages {
		
		stage ('stage-1') {

			steps {
				sh "mvn clean install"
				sh "sudo cp /root/.jenkins/workspace/pipeline_copy/target/LoginWebApp.war /root/servers/apache-tomcat-10.1.41/webapps/"
				sh "sudo cd /root/servers/apache-tomcat-10.1.41/bin/"
				sh "sudo ./startup.sh"
			}
		}
	}
}

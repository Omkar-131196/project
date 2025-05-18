pipeline {

	agent {

		label 'master'
	}
	
	environment {
		PATH = "/root/tools/apache-maven-3.9.9/bin:$PATH"
	}

	stages {

		stage ('stage-1') {

			steps {
				git url: 'https://github.com/Omkar-131196/project.git'
				withMaven {
			          sh "mvn clean install"
			        }
			}
		}
		
		stage ('stage-2') {

			steps {
				sh "sudo mvn clean install"
				sh "sudo cp /root/.jenkins/workspace/pipeline_copy/project/target/LoginWebApp.jar /root/servers/apache-tomcat-10.1.41/webapps/"
				sh "sudo cd /root/servers/apache-tomcat-10.1.41/bin/"
				sh "sudo ./startup.sh"
			}
		}
	}
}

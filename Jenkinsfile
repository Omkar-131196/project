pipeline {

	agent {

		label 'master'
	}

	stages {

		
		stage ('stage-1') {
			environment {
		PATH = "/root/tools/apache-maven-3.9.9/bin:$PATH"
			}

			steps {
				sh "sudo mvn clean install"
				sh "sudo cp /root/.jenkins/workspace/pipeline_copy/project/target/LoginWebApp.jar /root/servers/apache-tomcat-10.1.41/webapps/"
				sh "sudo cd /root/servers/apache-tomcat-10.1.41/bin/"
				sh "sudo ./startup.sh"
			}
		}
	}
}

pipeline {

	agent {

		label 'master'
	}

	stages {

		stage ('stage-1') {
			withMaven {
		          sh "mvn clean verify"
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

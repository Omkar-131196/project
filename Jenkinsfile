pipeline {

	agent {
		node {
		  label 'master'
		  customWorkspace '/root/project'
		}
	}

	environment {
	MAVEN_HOME = '/root/tools/apache-maven-3.9.9'
	PATH = "${env.PATH}:${MAVEN_HOME}/bin"		
	}

	stages {

		stage ('edit-database-file') {
			steps {
				script {
                    sh """
                        sed -i 's|jdbc:mysql://localhost:3306/test.*root", "root"|jdbc:mysql://database-1.cl424m4w4ro9.ap-south-1.rds.amazonaws.com:3306/test", "admin", "omkar1234"|' /root/project/src/main/webapp/userRegistration.jsp
                    """
                }
			}
		}

		stage ('build') {
			steps {
			sh "cd /root/project"
			sh "mvn clean install"
			}
		}

		stage ('deploy') {
			steps {
			sh "cp -r /root/project/target/LoginWebApp.war /root/servers/apache-tomcat-10.1.41/webapps/"
			}
		}

		stage ('start-server') {
			steps {
			sh "/root/servers/apache-tomcat-10.1.41/bin/startup.sh"
			}
		}
	}

}

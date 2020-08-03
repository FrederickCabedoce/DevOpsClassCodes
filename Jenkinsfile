pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
				git credentialsId: 'GitHubID', url: 'https://github.com/FrederickCabedoce/DevOpsClassCodes'
			    sh 'ls -lrt'
                
            }
        }
		
		stage('Compile') {
            steps {
               sh '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3/bin/mvn compile'
            
               sh 'ls -lrt'
            }
        }
		
		stage('Test') {
            steps {
                sh '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3/bin/mvn test'
            }
        }
		
		stage('Package') {
            steps {
                sh '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3/bin/mvn package'
            }
        }
		
		stage('Deploy') {
            steps {
                sh 'sudo cp /var/lib/jenkins/workspace/AddressBookPackage/target/addressbook.war /usr/share/tomcat/webapps'
                sh 'sudo rm -r /usr/share/tomcat/webapps/addressbook'

                sh 'sudo systemctl restart tomcat'
            }
        }
    }
}


pipeline{
	tools{jdk 'JAVA_HOME'
			maven 'M2_HOME'
	
	}
	agent any
	stages{
			stage('checkout')
				{
					steps{
						git 'https://github.com/nafishaparween/maven-jenkins.git'
						}
				}
		stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }
			stage('compile')
			{
				steps{
						sh 'mvn compile'
				}
			}
			stage('test')
			{
				steps{
						sh 'mvn test'
				}
			}
    stage('package')
			{
				steps
        {
						sh 'mvn package'
				}
			}
    stage('install')
			{
				steps
        {
						sh 'mvn install'
				}
			}

		stage('Deploy') {
    steps {
        sh '''
            echo "Copying JAR to Tomcat EC2..."

            scp -i /var/lib/jenkins/.ssh/id_rsa \
                    target/*.jar \
                    ec2-user@15.252.140.184:/home/ec2-user/tomcat/webapps/

            echo "JAR copied successfully!"
        '''
    }
}
			}
}

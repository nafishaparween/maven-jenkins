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

		stage('Deploy')
			{
				steps
        {				sh '''
						scp target/*.jar ec2-user@15.252.140.184:/opt/tomcat/webapps/   '''
				}
			}
			}
}

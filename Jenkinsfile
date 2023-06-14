node('master'){
	   
	   stage('Git checkout'){
	                  git 'https://github.com/Palanimks/GeneralSpringBootProgExce.git'
	              }

  stage('sonar')

{
withSonarQubeEnv('sonar')
{
sh '/opt/maven/bin/mvn clean verify sonar:sonar -Dsonar.password=admin -Dsonar.login=admin'
} // SonarQube taskId is automatically attached to the pipeline context
}
	   stage('Build approval') 
        {
                          input "Build the app?"
        }
	 
	   stage('Build'){
	             sh '/opt/maven/bin/mvn clean install'
	         }
	         	   stage('Deployment approval') 
        {
                          input "Deploy the app?"
        }
	            stage('Deploy'){
              sh '/opt/maven/bin/mvn clean deploy -DaltDeploymentRepository=internal.repo::default::http://admin:admin123@4.79.14.95:8081/nexus/content/repositories/snapshots/'
         }
	stage('Running java backend application'){
	sh 'export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -Dspring.profiles.active=uat -jar $WORKSPACE/target/*.jar &'
	}
	}

node{	   
	   stage('Git checkout'){
	                  git 'https://github.com/Palanimks/GeneralSpringBootProgExce.git'
	              }

  stage('sonar')

{

	   stage('Build approval') 
        {
                          input "Build the app?"
        }
	 
	   stage('Build'){
	             sh '/usr/share/maven clean install'
	         }
	         	   stage('Deployment approval') 
        {
                          input "Deploy the app?"
        }
	            stage('Deploy'){
              sh '/usr/share/maven clean deploy -DaltDeploymentRepository=internal.repo::default::http://admin:admin123@54.79.14.95:8081/nexus/content/repositories/snapshots/'
         }
	stage('Running java backend application'){
	sh 'export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -Dspring.profiles.active=uat -jar $WORKSPACE/target/*.jar &'
	}
   }
}
	



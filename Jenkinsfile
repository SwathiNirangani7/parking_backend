node{	   
	   stage('Git checkout'){
	                  git 'https://github.com/Palanimks/GeneralSpringBootProgExce.git'
	              }

  stage('sonar')

{
	mvn sonar:sonar \
  -Dsonar.projectKey=mvn_project \
	-Dsonar.login=5915cd7bb5a6b9d5b94daa1a2d2cf79097e32404 \
  -Dsonar.host.url=http://3.26.181.231:9000 
	    
}

	   stage('Build approval') 
        {
                          input "Build the app?"
        }
	 
	   stage('Build'){
	             sh "mvn clean install"
	         }
	         	   stage('Deployment approval') 
        {
                          input "Deploy the app?"
        }
	            stage('Deploy'){
              sh "mvn clean install deploy"
         }
	stage('Running java backend application'){
	sh 'export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -Dspring.profiles.active=uat -jar $WORKSPACE/target/*.jar &'
	}
   }
}
	



node{	   
	   stage('Git checkout'){
	                  git 'https://github.com/Palanimks/GeneralSpringBootProgExce.git'
	              }

  stage('sonar')
	{
				sh 'mvn clean verify sonar:sonar -Dmaven.test.skip=true'
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
	      sh "mvn clean deploy -DaltDeploymentRepository=releaseRspository::default::http://admin:admin123@3.27.106.34:8081/repository/maven-snapshots"
   
         }
	stage('Running java backend application'){
	sh 'export JENKINS_NODE_COOKIE=dontKillMe ;nohup java -Dspring.profiles.active=uat -jar $WORKSPACE/target/*.jar &'
	}
   }

	



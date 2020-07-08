pipeline {
    agent any
   
   
    stages {
	    //stage('remove'){
		 
        stage('build') {
            
		   agent {
			   docker { image 'sumavarshitha/java-tomcat-maven-example' }}
		steps {
			sh 'rm -rf assessmentdocker' 
	        sh 'git clone https://github.com/SumaVarshitha/java-tomcat-maven-example.git'
                sh "mvn clean package"
            
	    }
        }
        stage('SonarQube Analysis'){
		 environment{
               sonarscanner = tool 'sonars'
                   }
            steps{
               withSonarQubeEnv('sonar'){
                    sh '${sonarscanner}/bin/sonar-scanner -Dproject.settings=./sonar-project.properties'
		       //sh "${scannerHome}/bin/sonar-scanner"
               //sh 'mvn sonr:sonar' 
	       }
            }
        }

    }
        
      /*  stage("Quality Gate") {
            steps {
              timeout(time: 3, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
              }
            }
        }*/
       
}

pipeline {
    agent any
    
    tools {
        maven 'apache-maven-3.6.3' 
    }
    
    stages {
    	 
	   stage ('Clone') {
            steps {
                git branch: 'master', url: "https://github.com/zakaria2905/lab-7-1.git"
            }
	    }
	 
	   stage('Build & Unit test'){
		  steps {
				sh 'mvn clean verify -DskipITs=true';
		      	junit '**/target/surefire-reports/TEST-*.xml'
		      	archiveArtifacts  'target/*.jar'

	      }
   	  }
	
	  stage ('Integration Test'){
	      steps {
    			sh  'mvn clean verify -Dsurefire.skip=true';
				junit '**/target/failsafe-reports/TEST-*.xml'
      			archiveArtifacts  'target/*.jar'
      		}
      }	
    }
  }
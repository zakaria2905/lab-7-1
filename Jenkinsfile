pipeline {
    agent any
    
    tools {
        maven 'apache-maven-3.6.3' 
    }
    
    stages {
    	 
	   stage ('Clone') {
            steps {
                git branch: 'master', url: "https://gitlab.com/mromdhani/07-jenkins-maven-plugin-01-unit-and-integration-tests.git"
            }
	    }
	 
	   stage('Build & Unit test'){
		  steps {
				bat 'mvn clean verify -DskipITs=true';
		      	junit '**/target/surefire-reports/TEST-*.xml'
		      	archiveArtifacts  'target/*.jar'
	      }
   	  }
	
	  stage ('Integration Test'){
	      steps {
    			bat  'mvn clean verify -Dsurefire.skip=true';
				junit '**/target/failsafe-reports/TEST-*.xml'
      			archiveArtifacts  'target/*.jar'
      		}
      }	
    }
  }
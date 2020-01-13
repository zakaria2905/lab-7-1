pipeline {
    agent any
    stages {
    	 
	stage ('Clone') {
            steps {
                git branch: 'master', url: "https://github.com/jfrog/project-examples.git"
            }
        }
	 
	stage('Build & Unit test'){
		  steps {
				bat 'mvn clean verify -DskipITs=true';
		      	junit '**/target/surefire-reports/TEST-*.xml'
		      	archive 'target/*.jar'
	      }
   	}
	
	stage ('Integration Test'){
	      steps {
    			bat  'mvn clean verify -Dsurefire.skip=true';
				junit '**/target/failsafe-reports/TEST-*.xml'
      			archive 'target/*.jar'
      		}
      	}	
   }
  }
pipeline{
 tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
     agent any
	  
	  stages{
	  
	  stage("checkout"){
	   steps{
	   git 'https://github.com/ashisnishanka/maven-test.git'
	   }
	                  }
	
	   stage("compile"){
	    steps{
		 sh 'mvn compile'
		}
		}
       stage("test"){
	    steps{
		 sh 'mvn test'
		}
		}
	stage("build and SonarQube Analysis")
     {
   agent any
    steps {
	 withSonarQubeEnv('testsonarq')
	 {
	  sh "mvn clean package sonar:sonar -Dsonar.projectKey=jenkins-project1 -Dsonar.projectName='jenkins-project1'"
	 }
	}
  }
       stage("package"){
	    steps{
		 sh 'mvn clean package'
                 // #sh "mv target/*.war target/myweb.war"

		}
		}
stage(backup)
		  {
  steps{

	  nexusArtifactUploader artifacts: [[artifactId: 'app', classifier: '', file: 'app/target/app-1.0.jar', type: 'jar']], credentialsId: 'nexus', groupId: 'com.idream', nexusUrl: '52.66.179.54:8081/', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-releases', version: '1.0'
	  
  }
	
}
	}
	}

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
	
       stage("package"){
	    steps{
		 sh 'mvn clean package'
                 // #sh "mv target/*.war target/myweb.war"

		}
		}
stage(backup)
		  {
  steps{

	  nexusArtifactUploader artifacts: [[artifactId: 'app', classifier: '', file: 'target/app-1.0.jar', type: 'jar']], credentialsId: 'nexus', groupId: 'com.idream', nexusUrl: 'http://52.66.179.54:8081/', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-releases', version: '1.0'
	  
  }
	
}
	}
	}

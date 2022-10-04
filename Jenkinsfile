pipeline {
    agent any

    tools {
        maven "maven3"
    }

    stages {
        stage('clone') {
            steps {
                    git credentialsId: 'github_credentials', url: 'https://github.com/jmstechhome19/spring3-mvc-maven-xml-hello-world.git'
                 }
                
            }
		stage('build') {
		    steps {
			   sh "mvn clean package"
		    }
		}
		stage('deploy'){
		 steps{
		    sh "curl -v -u admin:admin -T /var/lib/jenkins/workspace/sping3_pipeline/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://65.2.121.152:8080/manager/text/deploy?path=/springapp&update=true'"
	    } 
	}
  }
    post {
                success {
                    archiveArtifacts 'target/*.war'
                }
    }  
}

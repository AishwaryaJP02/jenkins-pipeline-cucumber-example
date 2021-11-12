pipeline{

    agent any
       environment {
	    PATH = "/opt/maven/apache-maven-3.8.2/bin:$PATH"
       }

    stages {

        stage ('Compile Stage') {
	
            steps {

               
                    sh 'mvn clean install'

                

            }
        }
    stage ('Test Stage') {
	
            steps {

                
                    sh 'mvn test'

                   sh 'mvn allure:serve'	

            }
        }


        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'

            }

        }
	stage ('Allure reports')
	    {
		    steps{
			    script {
              allure([
                includeProperties: false,
                jdk: '',
                properties: [],
                reportBuildPolicy: 'ALWAYS',
                results: [[path: 'target/allure-results']]
              ])
            }
		    }
	    }
    }

}

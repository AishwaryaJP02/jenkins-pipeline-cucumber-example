pipeline{

    agent any
       environment {
	    PATH = "/opt/maven/bin:$PATH"
       }

    stages {

        stage ('Compile Stage') {
	tools {
                jdk "jdk8"
            }

            steps {

               
                    sh 'mvn clean install'

                

            }
        }
    stage ('Test Stage') {
	    tools {
                jdk "jdk8"
            }

            steps {

                
                    sh 'mvn test'

                

            }
        }


        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'

            }

        }

    }

}

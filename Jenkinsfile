pipeline {
	agent {
		node {
			label 'windows'
		}
	}
	
	options{
		timestamps()
	}
	
	
	stages{
		stage("Checkout, Test & Publish") {
			steps{
				checkout scm
				
				script{
					bat(/C:\Users\Siva Reddy\Downloads\apache-maven-3.6.2-bin\apache-maven-3.6.2\mvn clean  test /)
				}
				
				step([$class : 'Publisher', reportFilenamePattern : '**/testng-results.xml'])
			}
		}
		
		stage("Email"){
			steps{
				emailext (to: 'sivaece496@gmail.com', replyTo: 'noreplay@gmail.com', subject: "Email Report from - '${env.JOB_NAME}' ", body: readFile("target/surefire-reports/emailable-report.html"), mimeType: 'text/html');
			}
		}
	}
	

}

pipeline{
	
	agent any

	tools{
		maven 'maven'
	}

	stages{

		stage("Build"){
			steps{
				
				git 'https://github.com/jglick/simple-maven-project-with-tests.git'
				sh "mvn -Dmaven.test.failure.ignore=true clean package"
			}
			post{
				success{
					junit '**/target/surefire-reports/TEST-*.xml'
					archiveArtifacts 'target/*.jar'
				}
			}
		}

		stage("Deploy to QA"){
			steps{
				echo("deploy to QA")
			}
		}

		stage("Regression Automation Test"){
			steps{
				catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
					git 'https://github.com/RajManagoli2107/March2023POMSeries.git'
					sh "mvn clean test -Dsurefire.suiteXmlFiles=src/test/resources/testrunners/testng_regression.xml"
				}
				
			}
		}


		stage("Publish Allure Reports"){
			steps{
				script {
					allure([
						includeProperties: false,
						jdk: '',
						properties: [],
						reportBuildPolicy: 'ALWAYS',
						results: [[path: '/allure-results']]
					])
				}
			}
		}

		stage("Publish Extent Reports"){
			steps{
					publishHTML([allowMissing: false,
					keepAll: true,
					reportDir: 'reports',
					reportFiles: 'TestExecutionReport.html',
					reportName: 'HTML Regression Extent Report',
					reportTitles: ''])
			}
		}

		stage("Deploy to stage"){
			steps{
				echo("deploy to stage")
			}
		}

		stage("Sanity Automation Test"){
			steps{
				catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
					git 'https://github.com/RajManagoli2107/March2023POMSeries.git'
					sh "mvn clean test -Dsurefire.suiteXmlFiles=src/test/resources/testrunners/testng_sanity.xml"
				}
			}
		}

		stage("Publish Extent Reports"){
			steps{
					publishHTML([allowMissing: false,
					keepAll: true,
					reportDir: 'reports',
					reportFiles: 'TestExecutionReport.html',
					reportName: 'HTML Regression Extent Report',
					reportTitles: ''])
			}
		}
		
	}
}
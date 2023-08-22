pipeline{
	
	agent any

	stages{

		stage("build"){
			steps{
				echo("build the project")
			}
		}

		stage("Run the Unit test"){
			steps{
				echo("run UTs")
			}
		}

		stage("Run Integration test"){
			steps{
				echo("run ITs")
			}
		}

		stage("Deploy to Dev"){
			steps{
				echo("deploy to dev")
			}
		}

		stage("Deploy to QA"){
			steps{
				echo("deploy to QA")
			}
		}

		stage("Run regression test cases on QA"){
			steps{
				echo("run test cases on QA")
			}
		}

		stage("Deploy to stage"){
			steps{
				echo("deploy to stage")
			}
		}

		stage("Run regression test cases on Stage"){
			steps{
				echo("run test cases on stage")
			}
		}

		stage("Deploy to PROD"){
			steps{
				echo("deploy to PROD")
			}
		}
	}
}
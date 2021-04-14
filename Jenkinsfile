pipeline {
  agent any
  stages {
    stage("Clean workspace") {
      steps {
        echo 'Cleaning workspace'
        cleanWs()
      }
    }
    stage("Checkout") {
      steps {
        echo 'Checkout Updated Code'
        git branch: 'master', url:'https://github.com/Faisal-Saleem/devops-test'
      }
    }
    stage("Build App") {
      steps {
        echo 'Builing App...'
        bat 'dotnet build devops-test.sln'
	      bat 'dotnet publish -p:PublishProfile=IISProfile'
      }
    }
  }
}

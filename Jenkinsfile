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
        bat 'dotnet build devops-test/devops-test.sln'
      }
    }
    stage("Publish App to IIS") {
      steps {
        echo 'Publishin APP...'
        bat 'C:\\Windows\\System32\\inetsrv\\appcmd.exe stop apppool /apppool.name:testing'
        bat 'dotnet publish -p:PublishProfile=IISProfile devops-test/devops-test.sln'
      }
    }
  }
}

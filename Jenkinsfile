pipeline {
  agent any
  stages {
    stage('Clean workspace') {
      steps {
        echo 'Cleaning workspace'
        cleanWs()
      }
    }

    stage('Checkout') {
      steps {
        echo 'Checkout Updated Code'
        git(branch: 'master', url: 'https://github.com/Faisal-Saleem/devops-test')
      }
    }

    stage('Build App') {
      steps {
        echo 'Builing App...'
        bat 'dotnet build devops-test/devops-test.sln'
      }
    }

    stage('Publish App to IIS') {
      steps {
        echo 'Publishin APP...'
	echo 'Stopping App on IIS...'
        bat 'C:\\Windows\\System32\\inetsrv\\appcmd.exe stop apppool /apppool.name:testing'
	echo 'App Stopped...'
	echo 'Publishing...'
        bat 'dotnet publish devops-test/devops-test.sln -o c:\\inetpub\\wwwroot\\testing\\'
	echo 'Published...'
	echo 'Starting App on IIS...'
        bat 'C:\\Windows\\System32\\inetsrv\\appcmd.exe start apppool /apppool.name:testing'
	echo 'App Started...'
	echo 'Success...'
      }
    }

  }
}

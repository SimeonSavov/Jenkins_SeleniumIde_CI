pipeline {
    agent any

    stages {
        stage("Checkout code") {
            // checkout repo
            steps {
                git branch: 'main', url: 'https://github.com/SimeonSavov/Jenkins_SeleniumIde_CI'
            }
        }
        stage("Setup .Net Core") {
            // setup .Net core
            steps {
                bat '''
                echo Downloading .Net 6 Sdk
                curl -l -o dotnet-sdk-6.0.132-win-x86.exe https://download.visualstudio.microsoft.com/download/pr/ad59f1d1-5f19-4474-86be-2f09ab195618/5c7a64445dae84e386bb88e1f6ac09e4/dotnet-sdk-6.0.132-win-x86.exe
                echo Installing dotnet-sdk-6.0.132-win-x86.exe
                dotnet-sdk-6.0.132-win-x86.exe /quiet /norestart
                ''' 
            }
        }
        stage("Restore dependencies") {
            // restore dependencies
            steps {
                bat '''
                dotnet restore SeleniumIde.sln
                ''' 
            }
        }
        stage("Build") {
            // build
            steps {
                bat '''
                dotnet build SeleniumIde.sln --configuration Release
                ''' 
            }
        }
        stage("Run test") {
            // run tests
            steps {
                bat '''
                dotnet test SeleniumIde.sln --logger "trx;LOgFileName=TestResults.trx"
                ''' 
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/TestResults/*.trx', allowEmptyArchive: true
            step([
                $class: 'MSTestPublisher',
                testResultsFile: '**/TestResults/*.trx'
            ])
        }
    }
}
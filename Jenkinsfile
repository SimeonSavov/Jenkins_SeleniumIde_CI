pipeline {
    agent any

    stages{
        stage("Checkout code") {
            // checkout repo
            steps {
                git branch: 'main', url: 'https://github.com/SimeonSavov/Jenkins_SeleniumIde_CI'
            }
        }
        stage("Set up .Net Core") {
            // install .Net
        }
        stage("Restore dependencies") {
            // install dependencies
        }
        stage("Build") {
            // build
        }
        stage("Run tests") {
            // run tests
        }
    }
}
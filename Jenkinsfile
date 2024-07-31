pipeline {
    agent any

    stages {
        stage("Checkout code") {
            // checkout repo
            steps {
                git branch: 'main', url: 'https://github.com/SimeonSavov/Jenkins_SeleniumIde_CI'
            }
        }
    }
}
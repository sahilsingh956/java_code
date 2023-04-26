node {
        stage("Git Checkout"){
            checkout scmGit(branches: [[name: 'main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sahilsingh956/java_code.git']])
        }
        stage("Code Clean") {
            sh 'mvn clean'
        }
        stage("Code Build") {
            sh 'mvn install'
        }
        stage("Cleaning Workspace"){
            cleanWs()
        }
    }

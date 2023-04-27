pipeline {
    agent any
    stages {
        stage("Git Checkout") {
            steps {
                checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sahilsingh956/java_code.git']])
            }
        }
        stage('Package code') {
            steps {
                sh 'mvn clean install'
                sh 'aws cloudformation package --template-file Task1.yml --s3-bucket s3-bucketsahil1234 --output-template-file packaged-template.yml'
            }
        }
        stage('Deploy to S3') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAXLOIG5PCM2G6UFWF', credentialsId: 'asw-creds', secretKeyVariable: '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']]) {
                    sh 'aws s3 cp --recursive /var/lib/jenkins/workspace/Deploy_to_s3 s3://s3-bucketsahil1234'
                }
            }
        }
    }
}

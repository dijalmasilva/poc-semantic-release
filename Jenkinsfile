// The release stage in the pipeline will run only if the test stage in the pipeline is successful
pipeline {
    agent any 
    environment {
        GH_TOKEN = credentials('github-token')
        NPM_TOKEN = '82fef960-e2f7-43d1-aa69-df8183294adf'
    }
    stages {
        stage('Test') {
            steps {
                sh '''
                # Configure your test steps here (checkout, npm install, tests etc)
                npm install
                '''
                }
        }
        stage('Release') {
            tools {
            nodejs "node 10.18"
            }
            steps {
                sh '''
                # Run optional required steps before releasing
                npx semantic-release
                '''
            }            
        }
    }
}
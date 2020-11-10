pipeline {
    agent { dockerfile true }
    environment {
        GH_TOKEN = credentials('github-token')
        NPM_TOKEN = '82fef960-e2f7-43d1-aa69-df8183294adf'
    }
    stages {
        stage('Build') { 
            steps {
                sh '''
                # Run optional required steps before releasing
                npm install
                npx semantic-release
                '''
            }     
        }
    }
}
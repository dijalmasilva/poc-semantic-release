pipeline {
    agent { dockerfile true }
    environment {
        GH_TOKEN = credentials('github-token')
        NPM_TOKEN = '82fef960-e2f7-43d1-aa69-df8183294adf'
    }
    stages {
        stage('Release') {
            steps {
                sh '''
                # Run optional required steps before releasing
                echo $GH_TOKEN
                echo $NPM_TOKEN
                npm install
                npx semantic-release
                '''
            }            
        }
    }
}
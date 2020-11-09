pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
    environment {
        GH_TOKEN = credentials('github-token')
        NPM_TOKEN = '82fef960-e2f7-43d1-aa69-df8183294adf'
    }
    stages {
        stage('Build') { 
            steps {
                sh '''
                # Run optional required steps before releasing
                npx semantic-release
                '''
            }     
        }
    }
}
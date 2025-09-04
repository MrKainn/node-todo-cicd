pipeline {
    agent { label 'MyAgent1' }

    tools {
        // Jenkins will now automatically use the correct 'Default' tool
        // for the OS it's currently running on.
        git 'Linux-Git'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // This step will now run successfully on your Ubuntu agent
                echo "Checking out code on agent..."
                checkout scm
            }
        }

        stage('Verify Clone on Agent') {
            steps {
                sh 'echo "--- Running on Agent ---"'
                sh 'whoami'
                sh 'ls -la'
                sh 'git --version'
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}

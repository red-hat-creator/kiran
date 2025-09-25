pipeline {
    agent any

    environment {
        NODE_PORT = "${new Random().nextInt(6000) + 3000}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/HemanthYadavG7/hello-node.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                powershell 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'No build needed for Node.js app'
            }
        }

        stage('Run') {
            steps {
                echo "Running Node.js app on port $NODE_PORT"
                powershell "Start-Process -NoNewWindow -FilePath npm -ArgumentList 'start' -WorkingDirectory '${WORKSPACE}' -Environment @{PORT='$NODE_PORT'}"
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}

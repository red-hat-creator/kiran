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
                bat '"C:\\Program Files\\nodejs\\npm" install'
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
                bat """
                \$Env:PORT=$NODE_PORT
                npm start
                """
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}

pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'git@github.com:zhenzhengdeman/shuaibin.git'
            }
        }
        stage('Build') {
            steps {
                echo "Building project..."
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
            }
        }
    }
}


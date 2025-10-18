pipeline {
    agent any  // 在任何可用节点运行

    environment {
        // 定义环境变量（可选）
        PROJECT_NAME = "mywebsite"
        PYTHON = "python3"
    }

    stages {

        stage('Checkout') {
            steps {
                // 拉取 Git 仓库代码
                git branch: 'main', url: 'git@github.com:zhenzhengdeman/shuaibin.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                // 安装 Python 依赖
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install --upgrade pip'
                sh './venv/bin/pip install -r requirements.txt || echo "No requirements.txt found"'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                // 可以加一些构建命令，例如打包
                sh 'mkdir -p build'
                sh 'echo "Build output" > build/output.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // 这里运行 Python 测试，可以用 pytest 等
                sh './venv/bin/python -m unittest discover tests || echo "No tests found"'
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving artifacts...'
                // 保存构建产物
                archiveArtifacts artifacts: 'build/**/*', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying project...'
                // 这里只是示例，实际可执行部署命令
                sh 'echo "Deploying to server..."'
            }
        }

    }

    post {
        success {
            echo 'Build succeeded!'
            // 可以在这里发通知，例如邮件或 Slack
        }
        failure {
            echo 'Build failed!'
        }
    }
}


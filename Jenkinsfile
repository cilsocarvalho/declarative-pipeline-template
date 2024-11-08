pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'chmod a+x run_build_script.sh'
                sh './run_build_script.sh'
            }
        }
        stage('Test') {
            parallel {
                stage('Test On Windows') {
                    steps {
                        echo "Running tests on Windows"
                    }
                }
                stage('Test On Linux') {
                    steps {
                        echo "Running tests on Linux"
                    }
                }
            }
        }
        stage('Confirm Deploy') {
            steps {
                timeout(time: 60, unit: 'SECONDS') {
                    input(message: 'Okay to Deploy to staging?', ok: 'Let\'s Do it!')
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to Staging..."
                // Adicione o script de deploy aqui
            }
        }
        stage('Confirm Deploy to Production') {
            steps {
                timeout(time: 60, unit: 'SECONDS') {
                    input(message: 'Okay to Deploy to Production?', ok: 'Let\'s Do it!')
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to Production..."
                // Adicione o script de deploy aqui
            }
        }
    }
}

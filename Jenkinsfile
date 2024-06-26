pipeline{
    agent any
    stages {
        stage('Verify Branch'){
            steps{
                echo "$GIT_BRANCH"
            }
        }
        stage('Docker Build'){
            steps{
                sh 'docker compose build'
            }
        }
        stage('Run Unit Test'){
            steps{
                sh 'pytest ./test/sample.py'
            }
        }
        
    }
    post{
        success{
            echo "Test passed! :)"
        }
        failure{
            echo "Tests failed :("
        }
        always {
            sh 'docker compose down'
        }
    }
}

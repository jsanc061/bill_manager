pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
    post{
        success{
            echo 'Build SUCCESS'
        }
        failure{
            echo 'Build FAILURE'
        }
        unstable{
            echo 'Build was marked as UNSTABLE.'
        }
        changed{
            echo 'Current status of the Pipeline has CHANGED.'
            echo 'Previous Pipeline failed, but is now successful.'
        }
    }
}

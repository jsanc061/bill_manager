pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        tage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew check'
            }
        }
    }
    post{
        always {
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
            junit 'build/reports/**/*.xml'
        }
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

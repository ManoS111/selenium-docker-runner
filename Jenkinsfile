pipeline {
    agent any
    stages {
        stage('Start Grid') {
            steps{
                  bat "docker-compose -f grid.yaml up -d"
            }
            
        }
         stage('Run Test') {
            steps {
                  bat "docker-compose -f test-suites.yaml up"
            } 
        } 
    }
    post {
        always {
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
            archiveArtifacts artifacts: 'D:\\DockWorkspace\\06-jenkins-ci-cd\\01-jenkins\\volumes\\node\\workspace\\Selenium_Docker_Runner\\output\\vendor-portal\\emailable-report.html', followSymlinks: false
        }
    }
   
}
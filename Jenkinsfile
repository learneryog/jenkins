pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'echo "Building..."'
            sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
          }
        }

        stage('') {
          steps {
            sh 'echo "..."'
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            timeout(time: 1, unit: 'MINUTES') {
              retry(count: 5) {
                sh 'echo "Deploying..."'
              }

            }

          }
        }

        stage('') {
          steps {
            sh 'echo "..."'
          }
        }

      }
    }

    stage('') {
      steps {
        sh 'echo "dsf"'
      }
    }

  }
  post {
    always {
      echo 'This will always run'
    }

    success {
      echo 'This will run only if successful'
    }

    failure {
      echo 'This will run only if failed'
    }

    unstable {
      echo 'This will run only if the run was marked as unstable'
    }

    changed {
      echo 'This will run only if the state of the Pipeline has changed'
      echo 'For example, if the Pipeline was previously failing but is now successful'
    }

  }
}
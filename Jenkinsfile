pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        git(url: 'https://github.com/raphaelsander/Learning-PHP.git', branch: 'main')
      }
    }

    stage('Build') {
      parallel {
        stage('Build') {
          agent {
            dockerfile {
              filename 'Dockerfile'
            }

          }
          steps {
            echo 'Build'
          }
        }

        stage('View Dockerfile') {
          steps {
            sh 'cat Dockerfile'
          }
        }

      }
    }

  }
}
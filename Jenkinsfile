pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        git(url: 'https://github.com/raphaelsander/Learning-PHP.git', branch: 'main')
      }
    }

    stage('Build') {
      steps {
        echo 'Build'
        sh 'docker build -t "webdev:Dockerfile" .'
      }
    }

    stage('Run') {
      steps {
        sh 'docker run -d -p 80:80 --name webdev webdev:Dockerfile'
        input(message: 'Finished using the web site: (Click proceed to continue)', ok: 'Proceed')
      }
    }

    stage('Remove Container') {
      steps {
        sh 'docker container stop webdev'
        sh 'docker container rm webdev'
      }
    }

  }
}
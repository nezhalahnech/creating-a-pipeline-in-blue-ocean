pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Shell script') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }

    stage('Comprobacion manual') {
      steps {
        input 'Finished using the web site? (Click "Proceed" to continue)'
      }
    }

    stage('limpieza') {
      steps {
        sh './jenkins/scripts/kill.sh'
      }
    }

  }
}
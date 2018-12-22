pipeline {
  agent { dockerfile true }
  stages {
    stage('Build') {
      steps {
          sh 'mkdir build'
          sh 'cd build && cmake ..'
          timeout(time: 20, unit: 'MINUTES') {
            sh 'cd build && make -j8'
          }
      }
    }
    stage('Test') {
      steps {
        timeout(time: 30, unit: 'MINUTES') {
          sh 'cd build && make check -j8'
        }
      }
    }
  }
  post {
    always {
      echo 'Jenkins Finished'
    }
    success {
      echo 'Success!'
    }
    failure {
      echo 'Fail!'
    }
    unstable {
      echo 'Unstable!'
    }
  }
}

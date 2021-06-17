pipeline {
  agent any

  stages {
    stage('Do stuff') {
      environment {
        hermitEnvVars = sh(returnStdout: true, script: './bin/hermit env --raw').trim()
      }

      steps {
        // lets setup hermit
        withEnv(hermitEnvVars.split('\n').toList()) {

          sh 'jx version'

          echo 'done'
        }
      }
    }
  }
}


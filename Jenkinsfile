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

          echo 'about to invoke yq'
          sh 'yq --version'

          echo 'done'

          //sh 'echo the HERMIT_BIN = $HERMIT_BIN so there'
          //sh 'env | sort'
        }
      }
    }
  }
}


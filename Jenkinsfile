pipeline {
  agent any

  stages {
    stage('Do stuff') {
      environment {
        envVars = sh(returnStdout: true, script: './bin/hermit env --raw').trim()
      }

      steps {
        echo 'starting'
        echo "we have env vars $envVars"

        withEnv([envVars]) {
          sh 'pwd'

          echo 'hermit env is $HERMIT_BIN'
        }

        echo 'done'
      }
    }
  }
}


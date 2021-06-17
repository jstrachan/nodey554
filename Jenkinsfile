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

          sh 'echo the HERMIT_BIN = $HERMIT_BIN'
          sh 'env | sort'
        }

        echo 'done'
      }
    }
  }
}


pipeline {
  agent any

  stages {
    stage('Do stuff') {
      environment {
        text = sh(returnStdout: true, script: './bin/hermit env --raw')
        envVars = text.trim().split('\n').toList()

      }

      steps {
        echo 'starting'
        echo "env vars = $envVars"

        withEnv(envVars) {
          sh 'pwd'

          sh 'echo the HERMIT_BIN = $HERMIT_BIN so there'
          //sh 'env | sort'
        }

        echo 'done'
      }
    }
  }
}


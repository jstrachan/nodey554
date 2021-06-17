pipeline {
  agent any

  stages {
    stage('Do stuff') {
      environment {
        envVarText = sh(returnStdout: true, script: './bin/hermit env --raw').trim()
      }

      steps {
        echo 'starting'

        echo "env vars text = $envVarText"

        withEnv(envVarText.split('\n').toList()) {
          sh 'pwd'

          sh 'echo the HERMIT_BIN = $HERMIT_BIN so there'
          //sh 'env | sort'
        }

        echo 'done'
      }
    }
  }
}


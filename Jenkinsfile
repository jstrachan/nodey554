pipeline {
  agent any

  stages {
    stage('Do stuff') {
      steps {
        echo 'starting'

        text = sh(returnStdout: true, script: './bin/hermit env --raw')
        envVars = text.trim().split('\n').toList()
        
        echo "env vars type = $envVars.class"
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


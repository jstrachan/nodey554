pipeline {
  agent any

  stages {
    stage('Do stuff') {
      environment {
        envVars = sh(returnStdout: true, script: './bin/hermit env --raw').toString().trim().split("\n").toList()
      }

      steps {
        echo 'starting'
        //echo "we have env vars $envVars"

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


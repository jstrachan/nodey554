pipeline {
  agent any

  stages {
    stage('Do stuff') {
      steps{
        echo 'starting'

        envVars = sh(returnStdout: true, script: './bin/hermit env --raw').trim()

        echo "we have env vars $envVars"

        withEnv(envVars) {
          sh 'pwd'

          echo 'hermit env is $HERMIT_BIN'
        }

        echo 'done'
      }
    }
  }
}
pipeline {
  agent any

  stages {
    stage('Do stuff') {
      environment {
        hermitEnvVars = sh(returnStdout: true, script: './bin/hermit env --raw').trim()
      }

      steps {
        withCredentials([usernamePassword(credentialsId: '7ece71cf-5e9c-4778-9c61-83669674aa21', passwordVariable: 'GIT_TOKEN', usernameVariable: 'GIT_USER')]) {
          withEnv(hermitEnvVars.split('\n').toList()) {
            withEnv(["VERSION=" + sh(returnStdout: true, script: 'jx release version --tag').trim()]) {

              sh 'echo the version is $VERSION'

              sh '''                                                              
              echo "lets replace the helm chart version $VERSION"
              jx gitops yset -p version -v "$VERSION" ./charts/*/Chart.yaml
              jx gitops yset -p "image.tag" -v "$VERSION" ./charts/*/values.yaml
  
  
              echo "now lets commit and push the new tag"
              git add * || true
              git commit -a -m "chore: release $VERSION" --allow-empty
              git tag -fa v$VERSION -m "Release version $VERSION"
              git push --force origin v$VERSION
            '''
            }
          }
        }
      }
    }
  }
}


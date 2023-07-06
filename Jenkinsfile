pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'building'
        sh '''./gradlew.bat applyPatches
./gradlew.bat createReobfBundlerJar '''
      }
    }

    stage('post') {
      steps {
        archiveArtifacts(allowEmptyArchive: true, artifacts: 'build/libs/*.jar')
      }
    }

  }
}
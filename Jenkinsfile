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
        mail(subject: 'build success', body: 'build ${env.BUILD_URL} has completed sucsessfully', from: 'system@ci.zakariao.nl', replyTo: 'jenkins@zakariao.nl', to: 'z.aourzag@gmail.com')
      }
    }

  }
}
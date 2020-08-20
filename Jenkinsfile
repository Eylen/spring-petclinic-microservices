pipeline {
  agent {
    dockerfile true
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn -o clean package'
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts(artifacts: 'target/**/*.jar', onlyIfSuccessful: true, fingerprint: true)
      }
    }

  }
}

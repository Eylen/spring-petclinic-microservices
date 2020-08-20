pipeline {
  agent {
    dockerfile true
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts(artifacts: 'target/**/*.war', onlyIfSuccessful: true, fingerprint: true)
      }
    }

  }
}
pipeline {
  agent {
    dockerfile true
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn -f spring-petclinic-admin-server/pom.xml clean package'
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts(artifacts: '**/*.jar', onlyIfSuccessful: true, fingerprint: true)
      }
    }

  }
}

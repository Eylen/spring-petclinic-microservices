pipeline {
  agent {
    dockerfile
    {
        filename 'Dockerfile'
        args '--volume "$HOME"/.m2:/root/.m2'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn -f spring-petclinic-api-gateway/pom.xml clean package'
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts(artifacts: '**/*.jar', onlyIfSuccessful: true, fingerprint: true)
      }
    }

  }
}

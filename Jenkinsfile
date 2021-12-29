pipeline {
  agent { label 'myVM' }

  stages {
    stage('Continuos Integration') {
      stages {
        stage('Unit tests') {
          steps {
            sh 'mvn clean test'
            junit '**/target/surefire-reports/TEST-*.xml'
            jacoco(changeBuildStatus: true, maximumLineCoverage: '55', minimumLineCoverage: '55', runAlways: true)
          }
        }
        stage('Build') {
          steps {
            sh 'mvn clean package -Dmaven.test.skip=true'
            archiveArtifacts(artifacts: '**/*.jar', onlyIfSuccessful: true, fingerprint: true)
          }
        }
      }
    }
  }
}
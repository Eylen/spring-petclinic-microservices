pipeline {
  agent any
  stages {
    stage('Static Code Analysis') {
      agent {
        node {
          label 'master'
        }

      }
      steps {
        bat 'F:\\1.DevOps\\2020\\sonar-scanner-3.2.0.1227-windows\\bin\\sonar-scanner.bat -Dsonar.host.url=http://localhost:9000/ -Dsonar.login=d39153de87276ec525e77b1601b94e7ddfdd2f23 -Dsonar.projectVersion=1.0 -Dsonar.projectKey=sample-springboot-app -Dsonar.sources=spring-petclinic-admin-server/src/main/java/org/springframework/samples/petclinic/admin,spring-petclinic-api-gateway/src/main/java/org/springframework/samples/petclinic/api'
      }
    }

    stage('Build') {
      agent {
        dockerfile {
          filename 'Dockerfile'
          args '--volume "$HOME"/.m2:/root/.m2'
        }

      }
      steps {
        sh 'mvn clean package'
        junit '**/target/surefire-reports/TEST-*.xml'
        jacoco(changeBuildStatus: true, maximumLineCoverage: '55', minimumLineCoverage: '55', runAlways: true)
        archiveArtifacts(artifacts: '**/*.jar', onlyIfSuccessful: true, fingerprint: true)
      }
    }

  }
}
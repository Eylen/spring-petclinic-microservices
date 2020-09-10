pipeline {
  agent any
  stages {
    stage('UnitTests & Coverage') {
      agent {
        dockerfile {
          filename 'Dockerfile'
          args '--volume "$HOME"/.m2:/root/.m2'
        }

      }
      steps {
        sh 'mvn clean test'
        junit '**/target/surefire-reports/TEST-*.xml'
        jacoco(changeBuildStatus: true, maximumLineCoverage: '55', minimumLineCoverage: '55', runAlways: true)
      }
    }

    stage('Static Code Analysis') {
      agent {
        node {
          label 'master'
        }

      }
      steps {
        withSonarQubeEnv(installationName: 'Sonar8', credentialsId: 'SonarToken') {
          bat 'F:\\1.DevOps\\2020\\sonar-scanner-3.2.0.1227-windows\\bin\\sonar-scanner.bat -Dsonar.projectVersion=1.0 -Dsonar.projectKey=sample-springboot-app -Dsonar.java.binaries=. -Dsonar.junit.reportPaths=**/target/surefire-reports -Dsonar.coverage.jacoco.xmlReportPaths=**/target/coverage-reports/jacoco-unit.exec -Dsonar.sources=spring-petclinic-admin-server/src/main/java/org/springframework/samples/petclinic/admin,spring-petclinic-api-gateway/src/main/java/org/springframework/samples/petclinic/api'
        }

        waitForQualityGate(abortPipeline: true, credentialsId: 'SonarToken', webhookSecretId: 'SonarWebHook')
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
        sh 'mvn clean package -Dmaven.test.skip=true'
        archiveArtifacts(artifacts: '**/*.jar', onlyIfSuccessful: true, fingerprint: true)
      }
    }

  }
}
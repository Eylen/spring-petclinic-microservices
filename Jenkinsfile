pipeline {
        agent {
                node {
                        label 'myVM'
                }
        }
        stages {
                stage('Continuous Integration') {
                        stages {  
                                stage('Unit Tests'){		
                                        steps {
                                                bat 'mvn clean test'
                                                junit '**/target/surefire-reports/TEST-*.xml'
                                                jacoco(changeBuildStatus: true, maximumLineCoverage: '55', minimumLineCoverage: '55', runAlways: true)
                                        }
                                }
                                stage('Build'){		
                                        steps {
                                                bat 'mvn clean package -Dmaven.test.skip=true'
                                                archiveArtifacts(artifacts: '**/*.jar', onlyIfSuccessful: true, fingerprint: true)
                                        }
                                }
                        }
                }
        }
}

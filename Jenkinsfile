pipeline {
    agent any
    tools {
        gradle 'gradle'
        jdk 'jdk'
    }
    stages {
        stage('Build') {
            steps {
                sh 'gradle build --scan'
            }
        }
        stage('Test Path') {
            steps {
                sh 'pwd'
                sh 'ls'
            }
        }
        stage ('Publish Artifacts') {
        steps {
            rtUpload (
                buildName: JOB_NAME,
                buildNumber: BUILD_NUMBER,
                serverId: "artifactory", // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
                spec: """{
                            "files": [
                                {
                                    "pattern": "build/libs/springboots2idemo-0.1.1-SNAPSHOT.jar",
                                    "target": "gradle-local/springboots2idemo-0.1.1-SNAPSHOT.${BUILD_NUMBER}.jar",
                                    "recursive": "true"
                                }
                            ]
                    }"""   
                )
        }
     }
      stage ('pull artifact') {
        steps{
            rtDownload (
            serverId: "artifactory",
            spec: """{
                "files": [
                    {
                    "pattern": "gradle-local/springboots2idemo-0.1.1-SNAPSHOT.15.jar",
                    "target": "/var/jenkins_home/"
                    }
                ]
            }"""
        )
        }
    } 
    stage('Test Path') {
            steps {
                sh 'curl -O http://3.238.132.169:8082/artifactory/gradle-local/springboots2idemo-0.1.1-SNAPSHOT.16.jar'
                sh 'pwd'
            }
        }
  }
}

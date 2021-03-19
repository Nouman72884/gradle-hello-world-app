pipeline {
    agent any
    tools {
        gradle 'gradle'
        jdk 'JDK'
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
    //     stage ('Publish Artifacts') {
    //     steps {
    //         rtUpload (
    //             buildName: JOB_NAME,
    //             buildNumber: BUILD_NUMBER,
    //             serverId: "artifactory", // Obtain an Artifactory server instance, defined in Jenkins --> Manage:
    //             spec: """{
    //                         "files": [
    //                             {
    //                                 "pattern": "target/my-app-1.0-SNAPSHOT.jar",
    //                                 "target": "maven_local/my-app-1.0-SNAPSHOT.${BUILD_NUMBER}.jar",
    //                                 "recursive": "true"
    //                             }
    //                         ]
    //                 }"""   
    //             )
    //     }
    //  } 
  }
}

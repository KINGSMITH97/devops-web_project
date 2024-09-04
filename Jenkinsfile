pipeline {
    agent any

    stages {
        stage('Git clone') {
            steps {
                git branch: 'master', url: 'https://github.com/KINGSMITH97/devops-web_project.git'
            }
        }

        stage('Deploy to S3 bucket') {
            steps {
                s3Upload consoleLogLevel: 'INFO', dontSetBuildResultOnFailure: false, dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'devopswebsite', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-iso-east-1', showDirectlyInBrowser: false, sourceFile: '**/website*', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'jenkins-user', userMetadata: []
            }
        }
    }
}

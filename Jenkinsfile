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
                withAWS(credentials: 'jenkins-user', region: 'us-east-1') {
                    s3Upload(
                        file: '**/*',                        // Pattern to match files to upload
                        bucket: 'devopswebsite',             // Your S3 bucket name
                        path: '',                            // Destination path in the bucket (optional)
                        profileName: 'default',              // (Optional) Specify AWS profile
                        consoleLogLevel: 'INFO',             // Log level for console output
                        userMetadata: [                      // (Optional) User-defined metadata
                            'key': 'value'
                        ],
                        dontWaitForConcurrentBuildCompletion: false, // Wait for other builds to finish
                        pluginFailureResultConstraint: 'FAILURE',    // What happens if the plugin fails
                        dontSetBuildResultOnFailure: false           // Whether to mark build as failed on error
                    )
                }
            }
        }
    }
}

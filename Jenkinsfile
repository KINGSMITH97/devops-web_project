pipeline{
    agent any
    stages{

        stage('Git clone'){
            steps{
                git branch: 'master', url: 'https://github.com/KINGSMITH97/devops-web_project.git'
            }
        }

        stage('Deploy to S3 bucket'){
            steps {
                withAWS(credentials: 'jenkins-user', region: 'us-east-1') {
                    s3Upload(bucket: 'devopswebsite', path: '', includePathPattern: '**/*')
                }
            }
        }
    }
}
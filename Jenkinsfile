pipeline {
    agent any
//
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven3"
    }
    environment {
        S3_BUCKET_NAME = sh "date '+%Y%m%d%H%M'.zip"
    }

    stages {

        stage('Example') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo "Running ${env.BRANCH_NAME}"
                withAWS(credentials: 'DH_AWS', region: 'ap-northeast-2') {
s3Upload(path:"${S3_BUCKET_NAME}", file:"pom.xml",bucket:'solnae-test')
}
            }
        }

    }
}

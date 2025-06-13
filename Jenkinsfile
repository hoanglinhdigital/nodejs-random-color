pipeline {
    agent any
    stages {
        // stage('Checkout') {
        //     steps {
        //         git 'https://github.com/hoanglinhdigital/nodejs-random-color.git'
        //     }
        // }

        stage('Build') {
            steps {
                sh 'docker build -t nodejs-random-color:ver-${BUILD_ID} .'
            }
        }
        stage('Upload image to ECR') {
            steps {
                // Ensure AWS CLI is installed and configured
                sh 'aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 154061202936.dkr.ecr.ap-southeast-1.amazonaws.com'
                sh 'docker tag nodejs-random-color:ver-${BUILD_ID} 154061202936.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color:ver-${BUILD_ID}'
                sh 'docker push 154061202936.dkr.ecr.ap-southeast-1.amazonaws.com/nodejs-random-color:ver-${BUILD_ID}'

            }
        }
    }
}

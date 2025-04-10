pipeline {
    agent any
    parameters {
        string(name: 'DOCKER_IMAGE_VERSION', defaultValue: '', description: 'First parameter')
    }

    stages {
        stage('Update deploy.yaml') {
            steps {
                // Jenkins 파이프라인에서 작업 디렉토리를 변경할 때 사용한다.
                dir('university-api') {
                    echo "${params.DOCKER_IMAGE_VERSION}"
                    sh 'pwd'
                    sh 'ls -al'
                    sh "sed -i 's|kwonjimiin/university-api:.*|kwonjimiin/university-api:${params.DOCKER_IMAGE_VERSION}|g' deploy.yaml"
                    sh 'cat deploy.yaml'
                }
            }
        }
    }
}
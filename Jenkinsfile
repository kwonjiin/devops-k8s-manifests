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
                    sh 'git checkout main'
                    sh "sed -i 's|kwonjimiin/university-api:.*|kwonjimiin/university-api:${params.DOCKER_IMAGE_VERSION}|g' deploy.yaml"
                    sh 'cat deploy.yaml'
                }
            }

            stage('Commit & Push') {
                steps {
                    sh 'git config --list'
                    sh 'git config user.name "kwonjimiin"'
                    sh 'git config user.email "jimin001006@naver.com"'
                    sh 'git config --list'
                    sh 'git add .'
                    sh "git commit -m 'Update Image Version ${params.DOCKER_IMAGE_VERSION}'"
                    sh 'git status'
                    sh 'git push'
                }
            }
        }
    }
}
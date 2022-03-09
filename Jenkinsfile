pipeline {
    agent any
    stages {
        stage('deploy') {
            environment {
                BUILD_NUMBER_BASE = '0'
                VERSION_MAJOR = '0'
                VERSION_MINOR = '1'
                VERSION_PATCH = "${env.BUILD_NUMBER.toInteger() - BUILD_NUMBER_BASE.toInteger()}"
            }
            steps {
                script {
                    docker.withRegistry('', 'docker-hub') {
                        def customImage = docker.build("rajashekar0407/dockerhub:$VERSION_MAJOR.$VERSION_MINOR.$VERSION_PATCH")
                        customImage.push()
                    }
                }
            }
        }
    }
}

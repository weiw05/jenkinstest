pipeline {
    agent any
    environment {
        PATH = "/var/lib/jenkins/.pyenv/shims:${env.PATH}"
    }
    stages {
        stage('test') {
            steps {
                cmakeBuild buildDir: 'build',
                    sourceDir: '.',
                    cleanBuild: true,
                    installation: 'InSearchPath',
                    steps: [[args: 'all']]
            }
        }
    }
}
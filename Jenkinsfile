pipeline {
    agent any
    environment {
        PATH = "~/.pyenv/shims:~/.pyenv/bin:${env.PATH}"
    }
    stages {
        stage('test') {
            steps {
                nvm('v14') {
                    cmakeBuild buildDir: 'build',
                        sourceDir: '.',
                        cleanBuild: true,
                        installation: 'InSearchPath',
                        steps: [[args: 'all']]

                }
            }
        }
    }
}
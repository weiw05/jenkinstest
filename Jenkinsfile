pipeline {
    agent any
    stages {
        stage('test') {
            steps {
                nvm('v14') {
                    withEnv(["PATH=~/.pyenv/shims:~/.pyenv/bin:${env.PATH}"]) {
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
}
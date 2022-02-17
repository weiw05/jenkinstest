pipeline {
    agent any
    stages {
        stage('test') {
            steps {
                    withEnv(["PATH=/var/lib/jenkins/.pyenv/shims:/var/lib/jenkins/.pyenv/bin:${env.PATH}"]) {
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
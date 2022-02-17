pipeline {
    agent any

    stages {
        stage('test') {
            cmakeBuild buildDir: 'build',
                sourceDir: '.',
                cleanBuild: true,
                installation: 'InSearchPath',
                steps: [[args: 'all']]
        }
    }
}
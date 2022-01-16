// beforeOptions true takes precedence over beforeInput true and beforeAgent true.
// https://www.jenkins.io/doc/book/pipeline/syntax/#evaluating-when-before-the-options-directive

pipeline {
    agent none
    stages {
        stage('Build C Program') {
            steps {
                echo 'calling make'
                make
            }
        }
        stage('Deploy') {
            when {
                beforeOptions true
                branch 'testing'
            }
            options {
                lock label: 'testing-deploy-envs', quantity: 1, variable: 'deployEnv'
            }
            steps {
                echo "Deploying to ${deployEnv}"
            }
        }
    }
}

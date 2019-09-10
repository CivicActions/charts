pipeline {
    agent any
    stages {
        stage('Lint chart') {
            // Based on https://github.com/helm/charts/blob/master/.circleci/config.yml
            steps {
                sh 'docker run --rm -v "$WORKSPACE:/workdir" gcr.io/kubernetes-charts-ci/test-image:v3.3.2 ct lint --all'
            }
        }
    }
    post {
        always {
            sh 'docker run --rm -v "$WORKSPACE:/workdir" gcr.io/kubernetes-charts-ci/test-image:v3.3.2 git clean -xdf'
        }
    }
}

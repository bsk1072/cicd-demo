pipeline {
    agent {
    node {
      label 'test-node'
    }
  }
    stages {
        stage('checkout stage') {
            steps {
                checkout scm
            }
        }
        stage('development stage') {
            when {
                branch 'feature/*'
            }
            parallel {
                stage('Branch A') {
                    steps {
                        echo "On Branch A"
                    }
                }
                stage('Branch B') {
                    steps {
                        echo "On Branch B"
                    }
                }
            }
        }
        stage("release stage") {
            when {
                branch 'PR-*'
            }
            steps {
                echo "this is a peer review stage"
            }
        }
        stage("release stage") {
            when {
                branch 'release/*'
            }
            steps {
                echo "this is a release stage"
            }
        }
        stage("release stage") {
            when {
                branch 'master'
            }
            steps {
                echo "this is a master deploy stage"
            }
        }
    }
}

pipeline {
    agent {
    node {
      label 'master'
    }
  }
  
  //edit file for demo(to be deleted later)
    stages {
        stage('checkout stage') {
            steps {
                checkout scm
            }
        }
        stage('testing shared library') {
            steps {
                sayHello('Santhosh')}
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
        stage("UAT testing stage") {
            when {
                branch 'PR-*'
            }
            steps {
                echo "this is a peer review stage"
            }
        }
        stage("deploy to staging") {
            when {
                branch 'release/*'
            }
            steps {
                echo "this is a release stage"
            }
        }
        stage("staging steps") {
            when {
                branch 'master'
            }
            steps {
                echo "this is a master deploy stage"
            }
        }
    }
}

def sayHello(String) {
    echo "Hello, ${String}."
}

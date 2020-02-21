pipeline {
    agent {
    node {
      label 'Master'
    }
  }
    stages {
        stage('Non-Parallel Stage') {
            steps {
                checkout scm
            }
        }
        stage('Parallel Stage') {
            parallel {
                stage('Branch A') {
                    agent {
                        label "Agent-node"
                    }
                    steps {
                        echo "On Branch A"
                    }
                }
                stage('Branch B') {
                    agent {
                        label "Agent-node"
                    }
                    steps {
                        echo "On Branch B"
                    }
                }
                stage('Branch C') {
                    agent {
                        label "Agent-node"
                    }
                    stages {
                        stage('Nested 1') {
                            steps {
                                echo "In stage Nested 1 within Branch C"
                            }
                        }
                        stage('Nested 2') {
                            steps {
                                echo "In stage Nested 2 within Branch C"
                            }
                        }
                    }
                }
            }
        }
    }
}

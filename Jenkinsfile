pipeline {
    agent any
    stages {
        // First Stage
        stage("First Stage") {
            steps {
                sh """
                   echo "First stage"
                """
            }
        }

        // Second Stage
        stage("Second Stage") {
            steps {
                sh """
                   echo "Second stage"
                """
            }
        }

        // Parallel Jobs
        stage("Parallel Jobs") {
            parallel {
                stage("Job 1") {
                    steps {
                        echo 'Running Job 1'
                        // Add your job 1 steps here
                    }
                }
                stage("Job 2") {
                    steps {
                        echo 'Running Job 2'
                        // Add your job 2 steps here
                    }
                }
                stage("Job 3") {
                    steps {
                        echo 'Running Job 3'
                        // Add your job 3 steps here
                    }
                }
            }
        }

        // Docker Login Stage
        stage("Docker Login") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKERHUB_CREDENTIALS_PSW', usernameVariable: 'DOCKERHUB_CREDENTIALS_USR')]) {
                    sh """
                        echo "------------ Logging in to DockerHub ------------"
                        sudo docker login -u \$DOCKERHUB_CREDENTIALS_USR --password-stdin
                        echo "------------ Successfully Logged in to DockerHub ------------"
                    """
                }
            }
        }

        // Parallel Stage with Sequential Stage
        stage("Parallel Stage") {
            parallel {
                stage("One") {
                    steps {
                        sh """
                           echo "One"
                        """
                    }
                }
                stage("Two") {
                    steps {
                        sh """
                           echo "Two"
                        """
                    }
                }
                stage("Three") {
                    steps {
                        sh """
                           echo "Three"
                        """
                    }
                }
            }
        }

        // Sequential Stage
        stage("Sequential") {
            steps {
                sh """
                    echo "Sequential"
                """
            }
        }
    }
}

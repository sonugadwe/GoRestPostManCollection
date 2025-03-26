pipeline {
    agent any
    stages {

        stage('Build') {
            steps {
                echo "Building the war"
            }
        }

        stage("Deploy to QA") {
            steps {
                echo "Deploying to QA"
            }
        }

<<<<<<< HEAD
        stage('Checkout') {
            steps {
                git url: 'https://github.com/sonugadwe/GoRestPostManCollection'
            }
        }

        stage('Pull Docker Image') {
            steps {
                sh 'docker pull sgadwe/gorestdatadriventest:1.0'
            }
        }

        stage('Run API Test Cases') {
            steps {
                sh 'docker run -v $(pwd)/newman:/app/results sgadwe/gorestdatadriventest:1.0'
            }
        }

        stage('Publish HTML Extra Report') {
            steps {
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'newman',
                    reportFiles: 'gorest.html',
                    reportName: 'HTML Extra API Report',
                    reportTitles: ''
                ])
=======
        

        stage('Pull Docker Images') {
            parallel {
                stage('Pull GoRest Image') {
                    steps {
                        bat 'docker pull sgadwe/gorestdatadriventest:1.0'
                    }
                }
                stage('Pull Booking Image') {
                    steps {
                        bat 'docker pull sgadwe/mybookingapi:1.0'
                    }
                }
            }
        }

        stage('Prepare Newman Results Directory') {
            steps {
                bat 'mkdir -p $(pwd)/newman' 
            }
        }

        stage('Run API Test Cases in Parallel') {
            parallel {
                stage('Run GoRest Tests') {
                    steps {
                       bat 'docker run --rm -v %cd%/newman:/app/results sgadwe/gorestdatadriventest:1.0'
                    }
                }
                stage('Run Booking Tests') {
                    steps {
                       bat 'docker run --rm -v %cd%/newman:/app/results sgadwe/mybookingapi:1.0'
                    }
                }
            }
        }

        stage('Publish HTML Extra Reports') {
            parallel {
                stage('Publish GoRest Report') {
                    steps {
                        publishHTML([
                            allowMissing: false,
                            alwaysLinkToLastBuild: false,
                            keepAll: true,
                            reportDir: 'newman',
                            reportFiles: 'gorest.html',
                            reportName: 'GoRest API Report',
                            reportTitles: ''
                        ])
                    }
                }
                stage('Publish Booking Report') {
                    steps {
                        publishHTML([
                            allowMissing: false,
                            alwaysLinkToLastBuild: false,
                            keepAll: true,
                            reportDir: 'newman',
                            reportFiles: 'booking.html',
                            reportName: 'Booking API Report',
                            reportTitles: ''
                        ])
                    }
                }
>>>>>>> 493a71a5f4b674cd3663b213cb0cd33127676a4d
            }
        }

        stage("Deploy to PROD") {
            steps {
                echo "Deploying to PROD"
            }
        }
    }
}

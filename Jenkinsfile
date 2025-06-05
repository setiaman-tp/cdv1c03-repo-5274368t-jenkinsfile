pipeline {
    agent any
    stages {
        stage("ST1-5274368T") {
            steps {
                echo "ST1-5274368T: Setup Release Environment Completed"
            }
        }
        stage("ST2-5274368T") {
            steps {
                echo "To create container"
                docker commit 17de01d9cb08  server1-5274368t
                docker run -d -p 32700:80 server1-5274368t
                echo "ST2-5274368T: Server1 is successfully created"
            }
        }
        stage("ST3-5274368T") {
            steps {
                echo "ST3-5274368T: Server1 is healthy – Health check done"
            }
        }

        stage("ST4-Parallel-Checks") {
            parallel {
                stage("ST4A-5274368T") {
                    steps {
                        echo "ST4-5274368T: SQLI Check Completed"
                    }
                }
                stage("ST4B-5274368T") {
                    steps {
                        echo "ST4-5274368T: XSS Check Completed"
                    }
                }
            }
        }

        stage("ST5-5274368T") {
            steps {
                script {
                    def userInput = input(message: "Continue the pipeline?", ok: "Proceed", parameters: [
                        choice(name: "Confirm", choices: "Y\nN", description: "Choose Y to continue, N to stop")
                    ])
                    
                    if (userInput == "N") {
                        error("Pipeline stopped by user.")
                    }
                }
            }
        }

        stage("ST6-5274368T") {
            steps {
                echo "ST6-5274368T: Ready for next phase"
            }
        }
    }
}

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "test 1"
            }
        }
        stage('Test') {
            steps {
                echo "test 2"
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def jsonContent = readFile('output.json')
                    def data = readJSON text: jsonContent
                    echo "${data}"
                    executeCommands(data.common, "Common Commands")
                }
            }
        }
    }
}


def executeCommands(commands, stageName) {
    for (command in commands) {
        stage("${stageName} - ${command}") {
            steps {
                script {
                    echo "Executing Command: $command"
                    if (isWindows()) {
                        bat(command)
                    } else {
                        sh(command)
                    }
                }
            }
        }
    }
}

def isWindows() {
    return (isUnix() == false)
}

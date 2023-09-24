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
                def jsonContent = readFile('output.json')
                def data = readJSON text: jsonContent
                echo "${data}"
            }
        }
    }
}

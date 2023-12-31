// jenkins pipeline script
// pipeline with stages compile, test, package and echo messages in each stage
// use maven to compile, test and package the application
// define environment variables mavenHome and dockerHome for tools in jenkins

pipeline {
    agent any
    environment {
        mavenHome = tool 'mavenjenkins'
        dockerHome = tool 'dockerjenkins'
        PATH = "${mavenHome}/bin:${dockerHome}/bin:${PATH}}"
    }

    stages {

        stage('Info') {
            steps {
                echo 'Running on Jenkins'
                echo "$env.JENKINS_URL"
                echo "$env.JOB_NAME"
                echo "$env.BUILD_NUMBER"
                echo "$env.BUILD_ID"
                echo "$env.BUILD_URL"


            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling the application'
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the application'
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging the application'
                sh 'mvn package -DskipTests=true'
            }
        }
        stage('Echo') {
            steps {
                echo 'Echoing the application'
                sh 'echo "Hello World"'
            }
        }
    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
    }

}

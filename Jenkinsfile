pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v $HOME/.m2:/root/.m2:z -u root'
			reuseNode true
        }
    }
    stages {
        stage('Build') {
            steps {
				sh 'echo $BUILD_NUMBER'
                sh 'mvn -B -DskipTests clean package'
				sh 'echo $JOB_NAME'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
    }
}

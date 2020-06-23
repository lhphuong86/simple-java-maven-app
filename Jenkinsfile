pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
			sh 'echo $HOME'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
			sh 'echo $HOME'
                sh 'mvn -B -DskipTests clean package'
				sh 'echo $HOME'
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

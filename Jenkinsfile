pipeline {

    agent any

    tools { 
        maven 'my-maven' 
    }
    environment {
        MYSQL_ROOT_LOGIN = credentials('my-sql-root-login')
    }
    stages {

        stage('Build with Maven') {
            steps {
                sh 'mvn --version'
                sh 'java -version'
                sh 'mvn clean package'
            }
        }
       stage('Push Image') {
            steps {
                    sh 'docker build -t nguyenbangoc/springboot .'
                    sh 'docker push nguyenbangoc/springboot'
            }
        }
    }
}

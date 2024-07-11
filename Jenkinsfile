pipeline {

    agent any

    tools {
        maven 'my-maven'
        docker: 'Docker'
    }
    stages {
        // stage('clone git') {
        //     steps {
        //         git changelog: false, poll: false, url: 'https://github.com/NgocNB20/BDS-Jenkins.git'
        //     }
        // }

        stage('Build with Maven') {
            steps {
                sh 'mvn --version'
                sh 'java -version'
                sh 'mvn clean package'
            }
        }
       stage('Push Image') {
            steps {
                // This step should not normally be used in your script. Consult the inline help for details.
                withDockerRegistry(credentialsId: 'id_registry', url: ' https://index.docker.io/v1/)') {
                    sh 'docker build -t nguyenbangoc/springboot .'
                    sh 'docker push nguyenbangoc/springboot'
                }
            }
        }
    }
}

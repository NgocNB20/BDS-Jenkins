pipeline {
    agent any
    tools {
        maven 'my-maven'
    }
    stages {
        // stage('Build with Maven') {
        //     steps {
        //         sh 'mvn --version'
        //         sh 'java -version'
        //         sh 'mvn clean package'
        //     }
        // }
       stage('Push Image') {
            steps {
                // This step should not normally be used in your script. Consult the inline help for details.
                withDockerRegistry(credentialsId: 'id_registry', url: ' https://index.docker.io/v1/)') {
                    sh 'docker --version'
                    sh 'docker build -t nguyenbangoc/springboot .'
                    sh 'docker push nguyenbangoc/springboot'
                }
            }
        }
    }
}

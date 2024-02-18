pipeline{
    agent any
    tools{
        jdk 'jdk17'
        nodejs 'node16'
    }
    stages {
        stage('clean workspace'){
            steps{
                cleanWs()
            }
        }
        stage('Checkout from Git'){
            steps{
                git branch: 'main', url: 'https://github.com/Aj7Ay/Hotstar-Clone.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh "npm install"
            }
        }
        stage("Docker Build & Push"){
            steps{
                script{
                   withDockerRegistry(credentialsId: 'docker', toolName: 'docker'){
                       sh "docker build -t hotstar ."
                       sh "docker tag hotstar ash355/hotstar:latest "
                       sh "docker push ash355/hotstar:latest"
                    }
                }
            }
        }
    }
}

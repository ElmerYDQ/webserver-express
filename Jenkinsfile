pipeline {
    /*environment {
        registry = "3.136.118.102:5000/repo_entelgy"
        registryCredential = 'dockerprivate'
    }

    agent any
    
    stages {
        stage('Cloning Git') {
            steps {
                git 'https://github.com/ElmerYDQ/webserver-express.git'
            }
        }
        stage('Building image') {
            steps{
                script {
                dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }

        stage('Push Image') {
            steps{
                script {
                docker.withRegistry( '', registryCredential ) {
                    dockerImage.push(":$BUILD_NUMBER")
                    dockerImage.push(":latest")
                }
                }
            }
        }
        stage('Remove Unused docker image') {
            steps{
                sh "docker rmi $registry:$BUILD_NUMBER"
            }
        }
        stage('Deploy App on Kubernetes') {
            when {
                branch 'master'
            }
            steps {
                script {
                    kubernetesDeploy(configs: "app-prueba.yml", kubeconfigId: "kubeconfig")
                }
            }
        }
    }*/

    agent any

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Unit Testing') {
            steps {
                sh """
                echo "Running Unit Tests"
                """
            }
        }

        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "Building Artifact"
                """

                sh """
                echo "Deploying Code"
                """
            }
        }

        stage('rama feature/develop3') {
            when {
                branch 'feature/develop3'
            }
            steps {
                sh """
                echo "en la rama feature/develop3"
                """

                sh """
                echo "Deploying en la rama feature/develop3"
                """
             }
        }

        stage('rama feature/develop2') {
            when {
                branch 'feature/develop2'
            }
            steps {
                sh """
                echo "en la rama feature/develop2"
                """

                sh """
                echo "Deploying en la rama feature/develop2"
                """
            }
        }

        stage('rama feature/develop4') {
            when {
                branch 'feature/develop4'
            }
            steps {
                sh """
                echo "en la rama feature/develop4"
                """

                sh """
                echo "Deploying en la rama feature/develop4"
                """
            }
        }

    }   
}

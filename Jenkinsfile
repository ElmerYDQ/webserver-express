pipeline {
    environment {
        registry = "3.136.118.102:5000/repo_entelgy"
        registryCredential = 'dockerprivate'
    }

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
        
        stage('Cloning Git') {
            steps {
                git 'https://github.com/ElmerYDQ/webserver-express.git'
            }
        }

        stage('Building image') {
            when {
                branch 'master'
            }
            steps{
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }

        stage('Push Image') {
            when {
                branch 'master'
            }
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
            when {
                branch 'master'
            }
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

                sh """
                echo "Cambio en feature/develop4"
                """
            }
        }

        stage('Building image develop4') {
            when {
                branch 'feature/develop4'
            }
            steps{
                script {
                    dockerImageDevelop4 = docker.build registry + ":featureDevelop4"
                }
            }
        }

        stage('Push Image develop4') {
            when {
                branch 'feature/develop4'
            }
            steps{
                script {
                    docker.withRegistry( '', registryCredential ) {
                        dockerImageDevelop4.push(":featureDevelop4")
                    }
                }
            }
        }
        stage('Remove Unused docker image develop4') {
            when {
                branch 'feature/develop4'
            }
            steps{
                sh "docker rmi $registry:featureDevelop4"
            }
        }
    }  
}

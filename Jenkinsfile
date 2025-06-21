pipeline {
    agent any 
    tools {
        maven "mvn"
    }
    stages {
        stage("source code checkout") {
            steps {
                git branch: 'master', url: 'https://github.com/OnaifohChinweDevOpsProjects/CI-CD-Jenkins---K8s-Deployment'
            }
        }
        stage("maven build") {
            steps {
                sh "mvn clean package"
            }
        }
        stage("sonarqube") {
            steps {
                sh "mvn sonar:sonar"
            }
        }
        stage("docker build") {
            steps {
                sh "docker build -t devweb ."
            }
        }
        stage("docker push") {
            steps {
                sh "docker tag devweb ec2-18-215-154-157.compute-1.amazonaws.com:5000/devweb"
                withCredentials([usernamePassword(credentialsId: 'nexus_credential', passwordVariable: 'password', usernameVariable: 'username')]) {
                    sh 'echo "$password" | docker login -u "$username" ec2-18-215-154-157.compute-1.amazonaws.com:5000 --password-stdin'
                    sh "docker push ec2-18-215-154-157.compute-1.amazonaws.com:5000/devweb"
                }
            }        
        }
        stage("deploy") {
            steps {
                sh "microk8s kubectl apply -f devweb.yml"
                sh "microk8s kubectl get all -o wide"
            }
        }
    }
}

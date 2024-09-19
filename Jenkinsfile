pipeline { 
    agent any
    
    environment {
        SCANNER_HOME= tool 'sonar-scanner'
    }

    stages {
        
        stage('Git Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/GetPlaced60/10-MicroService-Appliction-latest.git'
            }
        }
        

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=10-Tier -Dsonar.projectName=10-Tier -Dsonar.java.binaries=. '''
                }
            }
        }

        stage('adservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/adservice') {
                    sh "docker build -t getplaced/adservice:latest ."
                    sh "docker push getplaced/adservice:latest"
                    sh "docker rmi getplaced/adservice:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('cartservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/cartservice/src/') {
                    sh "docker build -t getplaced/cartservice:latest ."
                    sh "docker push getplaced/cartservice:latest"
                    sh "docker rmi getplaced/cartservice:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('checkoutservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/checkoutservice') {
                    sh "docker build -t getplaced/checkoutservice:latest ."
                    sh "docker push getplaced/checkoutservice:latest"
                    sh "docker rmi getplaced/checkoutservice:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('currencyservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/currencyservice') {
                    sh "docker build -t getplaced/currencyservice:latest ."
                    sh "docker push getplaced/currencyservice:latest"
                    sh "docker rmi getplaced/currencyservice:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('emailservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/emailservice') {
                    sh "docker build -t getplaced/emailservice:latest ."
                    sh "docker push getplaced/emailservice:latest"
                    sh "docker rmi getplaced/emailservice:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('frontend') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/frontend') {
                    sh "docker build -t getplaced/frontend:latest ."
                    sh "docker push getplaced/frontend:latest"
                    sh "docker rmi getplaced/frontend:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('loadgenerator') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/loadgenerator') {
                    sh "docker build -t getplaced/loadgenerator:latest ."
                    sh "docker push getplaced/loadgenerator:latest"
                    sh "docker rmi getplaced/loadgenerator:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('paymentservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/paymentservice') {
                    sh "docker build -t getplaced/paymentservice:latest ."
                    sh "docker push getplaced/paymentservice:latest"
                    sh "docker rmi getplaced/paymentservice:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('productcatalogservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/productcatalogservice') {
                    sh "docker build -t getplaced/productcatalogservice:latest ."
                    sh "docker push getplaced/productcatalogservice:latest"
                    sh "docker rmi getplaced/productcatalogservice:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('recommendationservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/recommendationservice') {
                    sh "docker build -t getplaced/recommendationservice:latest ."
                    sh "docker push getplaced/recommendationservice:latest"
                    sh "docker rmi getplaced/recommendationservice:latest"
                       
                        }
                
                    }
                }
            }
        }

        stage('shippingservice') {
            steps {
                script{
                        
        withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                dir('/var/lib/jenkins/workspace/10-Tier/src/shippingservice') {
                    sh "docker build -t getplaced/shippingservice ."
                    sh "docker push getplaced/shippingservice"
                    sh "docker rmi getplaced/shippingservice"
                       
                        }
                
                    }
                }
            }
        }

        stage('sK8-Deploy') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'my-eks8', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://8617EBA266E7EF75DBB713D3E2A29110.gr7.ap-south-1.eks.amazonaws.com') {
                        sh 'kubectl apply -f deployment-service.yml'
                        sh 'kubectl get pods'
                        sh 'kubectl get svc'
                }
            }
        }

    }
}




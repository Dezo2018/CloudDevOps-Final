pipeline {
    agent any
        stages {
            stage('Linting') {
            steps {
                sh 'tidy -q -e *.html'
            }
            }
            stage('Build Image') {
                steps {
                    withCredentials(bindings: [[$class: 'UsernamePasswordMultiBinding', credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]) {
                        sh '''
                        docker build -t _cloud_devops .
                        '''
                    }
                }
            }
            stage('Push Image') {
                steps {
                    withCredentials(bindings: [[$class: 'UsernamePasswordMultiBinding', credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]) {
                        sh '''
                        docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
                        docker push desjenkins/capstone_cloud_devops
                        '''
                    }
            }
            }
            stage('Set current kubectl context') {
                steps {
                    withAWS(region: 'us-east-1', credentials: 'capstone') {
                        sh '''
                        kubectl config use-context arn:aws:eks:us-east-1:526037358249:cluster/extravagant-party-1603966107
                        '''
                    }
                }
            }
            stage ('Deploy blue container'){
                steps{
                    withAWS(region: 'us-east-1', credentials: 'capstone') {
                        sh '''
                kubectl apply -f ./blue-controller.json
                '''
                    }
                }
            }
            stage ('Deploy green container'){
                steps{
                    withAWS(region: 'us-east-1', credentials: 'capstone') {
                        sh '''
                kubectl apply -f ./green-controller.json
                '''
                    }
                }
        }
            stage ('Run blue service'){
                steps{
                    withAWS(region: 'us-east-1', credentials: 'capstone') {
                        sh '''
                kubectl apply -f ./blue-service.json
                '''
                    }
                }
        }
            stage ('Run green service'){
                steps{
                    withAWS(region: 'us-east-1', credentials: 'capstone') {
                        sh '''
                kubectl apply -f ./green-service.json
                '''
                    }
                }
        }
    }
}

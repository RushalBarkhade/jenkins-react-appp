pipeline{
    agent {
        any {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
    tools {nodejs "node12.22.2"}
    stages{       
        stage("install"){
            steps{
                sh 'echo INSTALLING'
                sh 'npm install --g yarn'
                sh "yarn"
            }   
        }
        stage("build"){
            steps{
                sh 'echo BUILDING'
                sh "yarn build"
            }
        } 
        stage('publish'){
                steps{
                    sh 'echo PUBLISHING'
                    // sh 'VARIALBE ${WORKSPACE}'
                    sh 'scp  -r /var/jenkins_home/workspace/jenkins-react/build/* ubuntu@3.111.23.153:/home/ubuntu/react-app'
                }
            }   
    }
}
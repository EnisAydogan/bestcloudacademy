pipeline {
    agent none
   
    stages {
        stage('Docker Build'){
            agent any
            steps {
                sh 'docker build -t enisaydogan/bestcloudforme:v2 .'
            }
            
        }
        stage ('Docker Push'){
            agent any
            steps {
                sh 'docker login -u $DockerHubUsername -p $DockerHubPassword'
                sh 'docker push enisaydogan/bestcloudforme:v2'
            }
        }
        stage('Docker Start'){
            agent any
            steps {
                sh 'docker login -u $DockerHubUsername -p $DockerHubPassword'
                sh 'docker pull enisaydogan/bestcloudforme:v2'
                sh 'docker run -d -p 5000:5000 --name flask  enisaydogan/bestcloudforme:v2'
            }
        }
        
    }
}

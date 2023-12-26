pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git 'https://github.com/C2-80522/SunProject.git'
            }   
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_4qJnvhKQsqhStNWW6b9fOXUZd60 | /usr/bin/docker login -u amita064 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t amita064/hackathon2 .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push amita064/hackathon2'
            }
        }
        stage ('docker remove container') {
            steps {
                sh '/usr/bin/docker container rm --force hackathon'
            }
        }
        stage ('docker create container') {
            steps {
                sh '/usr/bin/docker container run -itd --name hackathon -p 9876:80 amita064/hackathon2'
            }
        
       }
}

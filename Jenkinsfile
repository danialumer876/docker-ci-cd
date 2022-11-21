node 
{
    def app

    stage('Clone repository') {

        checkout scm
    }

    stage('Build image') {


        app = docker.build("html-docker-jenkins-ci-cd")
    }
    
    stage('Run Container') {
                
        def containerExists = sh(script: "docker ps -a -f name=html_docker_jenkins_ci_cd", returnStdout: true) == true

        if(containerExists){
            sh 'docker stop html_docker_jenkins_ci_cd'
            sh 'docker rm html_docker_jenkins_ci_cd'
            sh 'docker run --name html_docker_jenkins_ci_cd -p 8008:80 -d html-docker-jenkins-ci-cd'

        } else {
            sh 'docker run --name html_docker_jenkins_ci_cd -p 8008:80 -d html-docker-jenkins-ci-cd'
        }   
    }
  
}
    

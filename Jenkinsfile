node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("html-docker-jenkins-ci-cd")
    }
    
    stage('Run Container') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        
        def containerExists = sh(script: "docker ps -a -f name=html_docker_jenkins_ci_cd", returnStdout: true)

        if(!containerExists){
        // build the image
            sh 'docker stop html_docker_jenkins_ci_cd'
            sh 'docker rm html_docker_jenkins_ci_cd'
            sh 'docker run --name html_docker_jenkins_ci_cd -p 8008:80 -d html-docker-jenkins-ci-cd'

        } else {
            sh 'docker run --name html_docker_jenkins_ci_cd -p 8008:80 -d html-docker-jenkins-ci-cd'
        }   
    }
  
}

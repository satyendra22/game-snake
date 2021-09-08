node ('appServer-agent'){  
    def app
    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
       checkout scm
    }  
    
    stage('Build-and-Tag') {
    /* This builds the actual image; synonymous to
         * docker build on the command line */
        app = docker.build("satyendra22/game_snake")
    }
    stage('Push-to-dockerhub') {
    
    docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {
            app.push("latest")
        			}
         }
    stage('Pull-image-server') {
    
         sh "docker-compose down"
         sh "docker-compose up -d"	
      }
}

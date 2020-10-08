node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        git branch: 'patch-1', url: 'https://github.com/irfanansari568/nodeapp.git'
	    
 
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("irfanansari568/nodeapp")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
        docker.withRegistry('https://registry.hub.docker.com', 'Docker-hub') {
		sh "docker login -u ansari02 -p Dockerhub@1234"
		sh "docker push irfanansari568/nodeapp"
		
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}

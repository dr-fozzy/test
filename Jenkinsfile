node {
  checkout scm
  docker.image('abm/webapp', '
	  -d
	  --name ${env.BRANCH_NAME}
	  --restart=always
	  --expose 8080 
	  --rm 
	  -v $(pwd):/home/california/applications/california/current/public
	  -w /home/california/applications/california/current/public
	  -e VIRTUAL_HOST=${env.BRANCH_NAME}
  ').inside {
    sh 'nginx'
  }
}

node {
  checkout scm
  docker.image('abm/webapp').inside(" -d --name ${env.BRANCH_NAME} --restart=always --expose 8080 -v ${env.WORKSPACE}:/home/california/applications/california/current/public -w /home/california/applications/california/current/public -e VIRTUAL_HOST=${env.BRANCH_NAME} --entrypoint nginx")
  {
    sh 'tail -f /home/california/applications/california/current/logs/production.log'
  }
}

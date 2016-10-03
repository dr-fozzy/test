node {
  checkout scm
  def name = ("env.BRANCH_NAME =~ /(feature|hotfix)\/([a-zA-Z0-9_-]{0,})/)
  docker.image('abm/webapp').inside(" -d --name ${name} --restart=always --expose 8080 -v ${env.WORKSPACE}:/home/california/applications/california/current -w /home/california/applications/california/current -e VIRTUAL_HOST=${name} --entrypoint /bin/bash")
  {
    sh 'tail -f /home/california/applications/california/current/logs/production.log'
  }
}

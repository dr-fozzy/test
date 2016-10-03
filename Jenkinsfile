#!groovy
node {
  checkout scm

  def name = (env.BRANCH_NAME =~ "/(feature|hotfix)/([a-zA-Z0-9_-]{0,})/")
  name = name[0][2]

  docker.image('abm/webapp').inside("
                                    -d \
                                    --name ${name} \
                                    --restart=always \
                                    --expose 8080 -P \
                                    -v ${env.WORKSPACE}:/home/california/applications/california/current \
                                    -v /var/lib/jenkins/.ssh:/home/california/.ssh \
                                    -w /home/california/applications/california/current \
                                    -e VIRTUAL_HOST=${name}.qa.abmcloud.us \
                                    --entrypoint /bin/bash \
                                   ")
  {
    sh 'bundle install --deployment'
    sh 'tail -f /home/california/applications/california/current/logs/production.log'
  }
}

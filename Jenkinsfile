#!groovy
node {
  checkout scm
  
  shell "/var/lib/jenkins/.rvm/bin/rvm-shell"
  
  sh "env"
  sh "rvm use"
  sh "env"
}

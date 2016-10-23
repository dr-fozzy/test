#!groovy
node {
  checkout scm
  
  def RVM_ENV = sh ( script: "/bin/bash -li -c 'rvm use && env'", returnStdout: true).trim()
  
  properties([ 
    [
      $class: 'EnvInjectJobProperty',
      info: [loadFilesFromMaster: true, propertiesContent: RVM_ENV],
      keepBuildVariables: true, keepJenkinsSystemVariables: true,
      on: true
    ]
  ])
  
  
  sh "env"
}

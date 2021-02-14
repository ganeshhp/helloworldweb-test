
node ('buildserver') {

  stage ('SCM') {  
      checkout changelog: false, 
        poll: false, 
        scm: [$class: 'GitSCM', branches: [[name: '*/master']], 
        doGenerateSubmoduleConfigurations: false, extensions: [], 
        submoduleCfg: [], 
        userRemoteConfigs: [[url: 'https://github.com/ganeshhp/helloworldweb-test.git']]]
  }

  stage ('build') {
    bat 'mvn clean install'
  }

  stage ('deploy_to_artifactory') {
      bat 'curl -uuser1:AP9K5dA8z8tK69uEtYQzZ1jPeXA -T target/Helloworldwebapp.war "http://104.197.214.197:8081/artifactory/repo10/Helloworldwebapp.war"'
  }
  
  stage ('archive') {
    archiveArtifacts artifacts: 'target/Helloworldwebapp.war', followSymlinks: false
  }

}

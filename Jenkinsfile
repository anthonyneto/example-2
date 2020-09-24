pipeline {
  agent {
    docker {
      image 'ruby:latest'
      args '--entrypoint='
    }
  }
  stages {
    stage('gem') {
      steps {
        sh 'gem install http'\
      }
    }
    stage('ruby') {
      environment {
        GITHUB_OWNER = 'anthonyneto'
      }
      steps {
        withCredentials([string(credentialsId: 'github-token', variable: 'GITHUB_TOKEN')]) {
          sh 'curl -s https://gist.githubusercontent.com/anthonyneto/2024ee0afade6c5d3556344b20c079fa/raw/9d0a6a4a3e7b1436512c8986474c906cbcfe04b3/list-repos.rb | ruby'
        }
      }
    }
  }
}

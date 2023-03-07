node {
  
    stage('Checkout') {
        git branch: 'main', url: 'https://github.com/guddn1963/covid19-vaccine'
    }
    stage('Login'){
        sh 'echo jyhfpkcs%% | docker login -u guddn1963 --password-stdin' // docker hub 로그인
    }
    stage('Build Docker Image') {
        sh 'docker image build --network host -t guddn1963/django:latest .'
    }
    stage('Tag Docker Image') {
        sh 'docker image tag guddn1963/django:latest guddn1963/django:$BUILD_NUMBER'
    }
    stage('Publish Docker Image') {
        withDockerRegistry(credentialsId: 'docker-hub-token', url: 'https://index.docker.io/v1/') {
          sh 'docker image push guddn1963/django:$BUILD_NUMBER'
      }
    }
}




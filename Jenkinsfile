pipeline {
  agent any
  stages {
    stage("build") {
      steps {
        echo 'toto building'
      }
    }
    stage("test") {
      steps {
        echo 'toto test'
      }
    }
    stage("deploy") {
      steps {
        echo 'toto deploying'
      }
    }
  }
  post {
    always {
      echo 'always'
    }
    
    success {
      echo 'success'
    }
    
    failure {
      echo 'echec'
    }
  }
}

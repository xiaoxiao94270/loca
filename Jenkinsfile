pipeline {
  agent any
  
  environment {
	  NEW_V = '1.3'
	  SERVER_CREDENTIALS = credentials('server-credentials')
  }
  stages {
    stage("build") {
      steps {
        echo 'toto building'
        echo "version : ${NEW_V}"
	      echo "credentials : ${SERVER_CREDENTIALS}"
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
	withCredentials([
	usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PSW)
]) {
	echo "user: ${USER} password : ${PSW}"
}
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

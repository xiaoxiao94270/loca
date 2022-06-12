pipeline {
  agent any
  def gv
  environment {
	  NEW_V = '1.3'
	  SERVER_CREDENTIALS = credentials('server-credentials')
  }
  parameters {
	string(name: 'VERS', defaultValue: '', description: 'version to')
	choice(name: 'VERS2', choices: ['1.1','1.2'], description: 'des')
}

  stages {
    stage("build") {
      steps {
	script {
	gv = load "script.groovy"
}
        echo 'toto building'
        echo "version : ${NEW_V}"
	      echo "credentials : ${SERVER_CREDENTIALS}"
      }
    }
    stage("test") {
      when {
	expression {
		params.VERS == ''
	}
}
      steps {
        echo 'toto test'
	echo "VERS2: ${VERS2}"
      }
    }
    stage("deploy") {
      steps {
	      script {
	gv.buildApp()
}
        echo 'toto deploying'
	withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId:'server-credentials', usernameVariable: 'USERN', passwordVariable: 'PASSW']]) {
	echo "cf login some.awesome.url -u $USERN -p $PASSW"
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

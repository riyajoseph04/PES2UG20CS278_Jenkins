pipeline{
  agent any
  stages{
    stage('Build'){
      steps{
        sh 'g++ main/hello.cpp -o output'
        build 'PES2UG20CS278-1'
        echo 'Build successful'
      }
    }
    stage('Test'){
      steps{
        sh './output'
        echo 'Test successful'
      }
    }
    stage('Deploy'){
      when{
        expression{
          current_Build.result == null || currentBuild.result == 'SUCCESS'
        }
      }
      steps{
        echo 'Deploy successful'
      }
    }
  }
  post{
    failure{
      echo 'pipeline failed'
    }
  }
}

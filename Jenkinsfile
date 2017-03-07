node {
    stage('Checkotut') {
          // Checkout code from repository and update any submodules
          checkout scm
          sh 'git submodule update --init'  
          //build your gradle flavor, passes the current build number as a parameter to gradle
          //sh "./gradlew clean assembleMockDebug"
          sh "sleep 5s"
          
    }
    stage('Build'){
      parallel (
        "Compile & Package": {
            sh "echo Compile & Package"
            sh "sleep 2s"
        },
        "Run Unit Test": {
            sh "echo Run Unit Test"
            sh "sleep 4s"
        },
        "Static Code Analisys": {
            sh "Static Code Analisys"
            sh "sleep 3s"
        },
      )
    }
    stage('Create ST Env'){
        sh "echo Create ST Env"
        sh "sleep 3s"
    }
    stage('Deploy Code'){
        sh "echo Deploy Code"
        sh "sleep 5s"
    }
    stage('Load Test data'){
        sh "Load Test data"
        sh "sleep 5s"
    }
    stage('Run Test '){
        sh "echo Run Test"
        sh "sleep 5s"
    }

    stage('Create ST Env'){
      parallel (
        "Create clustered Env": {
            sh "echo Create clustered Env"
        },
        "Tear Down ST env": {
            sh "echo Tear Down ST env"
        },
      )
    }
    stage('Deploy Code'){
        sh "echo Deploy Code"
    }
    stage('ST Test'){
      parallel (
        "Run Perf Test": {
            sh "echo Run Perf Test"
            sh "sleep 2s"
        },
        "Run Security Test": {
            sh "echo Run Security Test"
            sh "sleep 4s"
        },
        "Run Ops Test": {
            sh "echo Run Ops Test"
            sh "sleep 3s"
        },
      )
    }
    stage('Prod Deploy'){
        sh "Prod Deploy"
    }

}

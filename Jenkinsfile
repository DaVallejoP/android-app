node('android') {
    stage('Build') {
          // Checkout code from repository and update any submodules
          checkout scm
          sh 'git submodule update --init'  
          //build your gradle flavor, passes the current build number as a parameter to gradle
          //sh "./gradlew clean assembleMockDebug"
          sleep(5,SECONDS)
          
    }
    stage('Test'){
      parallel (
        "JUnit": {
            sh "echo JUnit"
            sleep(2,SECONDS)
        },
        "DBUnit": {
            sh "echo DBUnit"
            sleep(4,SECONDS)
        },
        "Jasmine": {
            sh "echo Jasmine"
            sleep(3,SECONDS)
        },
      )
    }
    stage('Browser Tests'){
      parallel (
        "Firefox": {
            sh "echo Firefox"
        },
        "Edge": {
            sh "echo Edge"
        },
        "Safari": {
            sh "echo Safari"
        },
        "Chrome": {
            sh "echo Chrome"
        },
      )
    }
    stage('Dev'){
        sh "echo Dev"
    }
    stage('Staging'){
        sh "echo Staging"
    }
    stage('Production'){
        sh "echo Production"
    }
}

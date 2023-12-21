pipeline {
   agent any
      environment {
         PATH='/usr/local/bin:/usr/bin:/bin'
      }
   tools {
      nodejs '18.18.2'
   }
   stages {
      stage('NPM Setup') {
      steps {
         sh 'npm install'
      }
   }

//    stage('IOS Build') {
//    steps {
//       sh 'npx ionic capacitor build ios --release'
//      } 
//   }

   stage('Android Build') {
   steps {
      sh 'npx ionic capacitor copy android --prod && cd android && ./gradlew assembleRelease && cd ..'
   }
  }

   stage('APK Sign') {
   steps {
      sh 'C:/Program Files/Java/jdk-17/bin/jarsigner -storepass  -keystore my-release-key.keystore android/app/build/outputs/apk/release/app-release-unsigned.apk nameApp'
   }
   }

   stage('Stage Web Build') {
      steps {
        sh 'npm run build --prod'
    }
  }

//    stage('Publish Firebase Web') {
//       steps {
//       sh 'firebase deploy --token "Your Token Key"'
//    }
//   }

   stage('Publish iOS') {
      steps {
       echo "Publish iOS Action"
    }
   }

   stage('Publish Android') {
     steps {
    echo "Publish Android API Action"
   }
  }

 }
}


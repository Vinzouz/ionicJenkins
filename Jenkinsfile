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

//    stage('APK Sign') {
//     steps {
//       sh 'C:/Prog*les/Java/jdk-17/bin/jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore -storepass 123456 android/app/build/outputs/apk/release/app-release-unsigned.apk my-key-alias'
//     }
//    }

//    stage('APK Align and Verify') {
//     steps {
//         sh '''
//         C:/Users/Vincent/AppData/Local/Android/Sdk/build-tools/33.0.0/zipalign -v 4 android/app/build/outputs/apk/release/app-release-unsigned.apk android/app/build/outputs/apk/release/app-release.apk
//         C:/Users/Vincent/AppData/Local/Android/Sdk/build-tools/33.0.0/apksigner.bat verify android/app/build/outputs/apk/release/app-release.apk
//         '''
//     }
// }

   stage('Align and Sign APK') {
    steps {
        script {
            sh '''
            C:/Users/Vincent/AppData/Local/Android/Sdk/build-tools/33.0.0/zipalign -v 4 android/app/build/outputs/apk/release/app-release-unsigned.apk android/app/build/outputs/apk/release/app-aligned.apk
            C:/Users/Vincent/AppData/Local/Android/Sdk/build-tools/33.0.0/apksigner.bat sign --ks my-release-key.keystore --ks-key-alias my_key_alias --ks-pass pass:123456 --key-pass pass:123456 --out android/app/build/outputs/apk/release/app-signed.apk android/app/build/outputs/apk/release/app-aligned.apk
            C:/Users/Vincent/AppData/Local/Android/Sdk/build-tools/33.0.0/apksigner.bat verify android/app/build/outputs/apk/release/app-signed.apk
            '''
        }
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


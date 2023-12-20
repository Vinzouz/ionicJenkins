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

   stage('IOS Build') {
   steps {
      sh 'npx ionic capacitor build ios --release'
     } 
  }

   stage('Android Build') {
   steps {
      sh 'npx ionic capacitor build android --release'
   }
  }

   stage('APK Sign') {
   steps {
      sh '%JAVA_HOME%\bin\jarsigner -storepass your_password -keystore keys/yourkey.keystore platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk nameApp'
   }
   }

   stage('Stage Web Build') {
      steps {
        sh 'npm run build --prod'
    }
  }

   stage('Publish Firebase Web') {
      steps {
      sh 'firebase deploy --token "Your Token Key"'
   }
  }

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


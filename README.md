React Native FCM with Twilio

This project integrates Firebase Cloud Messaging (FCM) with Twilio for push notifications in React Native apps.

Features

Receive push notifications

Show local notifications

Schedule notifications

Handle notification click events

Installation

npm install react-native-fcm-twilio --save

Firebase Setup

Go to Firebase Console

Add a new project or use an existing one

Download google-services.json from Firebase

Place it inside your android/app/ directory

Android Setup

android/build.gradle

classpath 'com.google.gms:google-services:4.3.10'

android/app/build.gradle

apply plugin: 'com.google.gms.google-services'
dependencies {
  implementation 'com.google.firebase:firebase-messaging:23.0.0'
}

AndroidManifest.xml

Add inside <application>:

<service
  android:name="com.aotasoft.fcm.twilio.MessagingService"
  android:exported="true">
  <intent-filter>
    <action android:name="com.google.firebase.MESSAGING_EVENT"/>
  </intent-filter>
</service>

Basic Usage

import FCM, {FCMEvent} from 'react-native-fcm';

FCM.on(FCMEvent.Notification, notif => {
  console.log('Notification received:', notif);
});

FCM.getFCMToken().then(token => {
  console.log('FCM Token:', token);
});

You can also show local notifications, schedule them, or listen for token refresh.
---

// binding
buildFeatures {
viewBinding true
}

---

// coil
implementation("io.coil-kt:coil:2.2.2")

---

// glide
    implementation 'com.github.bumptech.glide:glide:4.15.0'
    annotationProcessor 'com.github.bumptech.glide:compiler:4.15.0'

---

// nav graph
    implementation 'androidx.navigation:navigation-fragment-ktx:2.5.3'
    implementation 'androidx.navigation:navigation-ui-ktx:2.5.3'
    
---

//nav component
    def nav_version = "2.5.3"

    implementation("androidx.navigation:navigation-fragment-ktx:$nav_version")
    implementation("androidx.navigation:navigation-ui-ktx:$nav_version")
    implementation("androidx.fragment:fragment-ktx:1.5.5")
    
---

// picasso
    implementation 'com.squareup.picasso:picasso:2.8'

---

// retrofit
    implementation "com.squareup.retrofit2:retrofit:2.9.0"
    implementation "com.squareup.retrofit2:converter-gson:2.9.0"
    
---

//circleimageview
    implementation 'de.hdodenhof:circleimageview:3.1.0'

---

//circleindicator
    implementation 'me.relex:circleindicator:2.1.6'

---

//room
    def room_version = "2.4.3"

    implementation "androidx.room:room-runtime:$room_version"
    annotationProcessor "androidx.room:room-compiler:$room_version"
---

// To use Kotlin annotation processing tool (kapt)
    kapt "androidx.room:room-compiler:$room_version"
    
---

//lottie animation
    def lottieVersion = "3.4.0"
    implementation "com.airbnb.android:lottie:$lottieVersion"

---

//firebase
    implementation platform('com.google.firebase:firebase-bom:31.1.1')
    implementation 'com.google.firebase:firebase-auth'
    implementation 'com.google.android.gms:play-services-auth:20.4.0'
    
---

//firebase firestore
    implementation 'com.google.firebase:firebase-messaging-ktx:23.1.1'
    implementation 'com.google.firebase:firebase-firestore'
    implementation 'com.google.firebase:firebase-firestore-ktx:24.4.1'

---

// google services
    classpath 'com.google.gms:google-services:4.3.10'
    
---

//DI (Hilt)
    implementation("com.google.dagger:hilt-android:2.44")
    kapt("com.google.dagger:hilt-android-compiler:2.44")
    implementation("com.tbuonomo:dotsindicator:4.3")
    id("com.google.dagger.hilt.android") version "2.44" apply false
    
---

// Lifecycle
    implementation 'androidx.lifecycle:lifecycle-livedata-ktx:2.5.1'
    implementation 'androidx.lifecycle:lifecycle-viewmodel-ktx:2.5.1'
    
---

// Interceptor
    implementation("com.squareup.okhttp3:logging-interceptor:5.0.0-alpha.2")
    
---

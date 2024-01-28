<script setup lang="ts">
  
  // Import the functions you need from the SDKs you need
  import { initializeApp } from "firebase/app";
  import { getAnalytics } from "firebase/analytics";


  
  // Your web app's Firebase configuration
  const firebaseConfig = {
  apiKey: "AIzaSyBJnDXvkKxYFD2R8YZWNbUpYkno6XSLoGg",
  authDomain: "newsapp-45c7a.firebaseapp.com",
  projectId: "newsapp-45c7a",
  storageBucket: "newsapp-45c7a.appspot.com",
  messagingSenderId: "857960706551",
  appId: "1:857960706551:web:9783da03771b6c86b67ef2",
  measurementId: "G-ZPVQXRL3C1"
};
  

  // Initialize Firebase
  const app = initializeApp(firebaseConfig);
  const analytics = getAnalytics(app);
  const provider = new GoogleAuthProvider();

  import { getAuth, getRedirectResult, GoogleAuthProvider } from "firebase/auth";
  const auth = getAuth();


  
  
  // handle null; before signing in ...

  getRedirectResult(auth)
    .then((result) => {
      // This gives you a Google Access Token. You can use it to access Google APIs.
      const credential = GoogleAuthProvider.credentialFromResult(result);
      const token = credential.accessToken;

      // The signed-in user info.
      const user = result.user;
      // IdP data available using getAdditionalUserInfo(result)
      
    }).catch((error) => {
      // Handle Errors here.
      const errorCode = error.code;
      const errorMessage = error.message;
      // The email of the user's account used.
      const email = error.customData.email;
      // The AuthCredential type that was used.
      const credential = GoogleAuthProvider.credentialFromError(error);
      
    });

  // signInWithPopup
  // import { getAuth, signInWithPopup, GoogleAuthProvider } from "firebase/auth";
  // const auth = getAuth();
  // signInWithPopup(auth, provider)
  // .then((result) => {
  //   // This gives you a Google Access Token. You can use it to access the Google API.
  //   const credential = GoogleAuthProvider.credentialFromResult(result);
  //   const token = credential.accessToken;
  //   // The signed-in user info.
  //   const user = result.user;
  //   // IdP data available using getAdditionalUserInfo(result)
  //   // ...
  // }).catch((error) => {
  //   // Handle Errors here.
  //   const errorCode = error.code;
  //   const errorMessage = error.message;
  //   // The email of the user's account used.
  //   const email = error.customData.email;
  //   // The AuthCredential type that was used.
  //   const credential = GoogleAuthProvider.credentialFromError(error);
  //
  // });

</script>

<template>
  <div id="container">
    <h1 id="login">LOGIN</h1>
    
    <div id="frame">
      <button id="button">Signin with Google</button>
    </div>

  </div>
    
</template>

<style scoped>

/* @media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  } */

#container{
  height: 100%;
  width: 100%;
  text-align: center;
}

#frame {
  height: 80vh;
  width: 80vw;
  background-color: #fff;
  margin: 20px auto;
}

  #button {
    display: block;
    
  }

</style>
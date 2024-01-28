<template>
  <main>
    <h2 id="login">LOGIN</h2>

    <div id="login-frame">
      <button ref="Btn" @click="logClicked">Sign in with Google</button>
    </div>
  </main>
</template>

<script>
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
import { getAnalytics } from "firebase/analytics";
import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, GoogleAuthProvider, signInWithRedirect, getRedirectResult } from "firebase/auth";

export default {
  data() {
    
  },

  mounted() {
    // TODO: Add SDKs for Firebase products that you want to use
    // https://firebase.google.com/docs/web/setup#available-libraries

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

    this.googleAuthCallback()
  },

  methods: {
    googleAuthCallback: async function () {
      const auth = getAuth()
      // After returning from the redirect when your app initializes you can obtain the result
      const result = await getRedirectResult(auth);
      console.log('result', result);

      if (result) {
        // This is the signed-in user
        const user = result.user;
        // This gives you a Google Access Token.
        const credential = GoogleAuthProvider.credentialFromResult(result);
        const token = credential.accessToken;

        console.log(user);
      }
    },

    logClicked: async function (e) {
      e.preventDefault()

      console.log('Clicked')

      const auth = getAuth();
      // Sign in using a redirect.
      const provider = new GoogleAuthProvider();
      // Start a sign in process for an unauthenticated user.
      provider.addScope('profile');
      provider.addScope('email');

      signInWithRedirect(auth, provider);
      // This will trigger a full page redirect away from your app
    },
    
    // register: async function (e) {
    //   e.preventDefault()

    //   const auth = getAuth();

    //   try {
    //     const userCredential = await createUserWithEmailAndPassword(auth, this.email, this.password);
    //     const user = userCredential.user
    //     console.log('User registered: ', user);
    //   } catch (error) {
    //     console.log('Error while registering user: ', error);
    //   }
    // },

    // login: async function (e) {
    //   e.preventDefault()

    //   const auth = getAuth();

    //   try {
    //     const userCredential = await signInWithEmailAndPassword(auth, this.email, this.password);
    //     const user = userCredential.user
    //     console.log('User signed in: ', user);
    //   } catch (error) {
    //     var errorMessage = error.message;
    //     console.log(errorMessage);
    //     console.log('Error while signing user- ', error);
    //   }
    // }
  }
}
</script>


<style scoped>
main {
  height: 100vh;
  width: 100vw;
  margin: 20px auto;
  /* background-color: brown; */
}

#login {
  text-align: center;
  margin: 20px auto;
  
}

#login-frame {
  height: 60vh;
  width: 60vw;
  background-color: aliceblue;
  text-align: center;
  margin: auto;
  padding-top: 27vh;
  
}
</style>
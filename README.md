
[![Author](https://img.shields.io/badge/author-9r3i-lightgrey.svg)](https://github.com/9r3i)
[![License](https://img.shields.io/github/license/9r3i/force-firesite.svg)](https://github.com/9r3i/force-firesite/blob/master/LICENSE)
[![Forks](https://img.shields.io/github/forks/9r3i/force-firesite.svg)](https://github.com/9r3i/force-firesite/network)
[![Stars](https://img.shields.io/github/stars/9r3i/force-firesite.svg)](https://github.com/9r3i/force-firesite/stargazers)
[![Issues](https://img.shields.io/github/issues/9r3i/force-firesite.svg)](https://github.com/9r3i/force-firesite/issues)
[![Release](https://img.shields.io/github/release/9r3i/force-firesite.svg)](https://github.com/9r3i/force-firesite/releases)
[![Donate](https://img.shields.io/badge/donate-paypal-orange.svg)](https://paypal.me/9r3i)



# force-firesite
ForceWebsite with Firebase data storage


# Configure
Same as [ForceWebsite](https://github.com/9r3i/force-website), this Firesite is as Force Application.

Configuration will be similiar, just edit the ```app.namespace``` and ```app.host```
```js
(async function(n,h,cnf,f){
  var ctag=document.getElementById(c), // script tag of website configuration, see configuration section
  ftag=document.getElementById(f), // script tag to load force script
  fname='force/virtual/force.js', // virtual path
  fscript=localStorage.getItem(fname), // get the force script if it's already stored in virtual file
  cnf=JSON.parse(ctag.textContent); // parse the config
  if(!fscript){ // check if it's not stored yet
    fscript=await fetch(cnf.force.file).then(r=>r.text()); // fetch the force.js file
    localStorage.setItem(fname,fscript); // store the force script into virtual file, so next time it won't be loaded anymore
  }
  ftag.textContent=fscript; // load the force script, immedietly executed by the browser
  const app=(new Force).app(n,h,cnf); // prepare the app using Force app instance
  await app.init(); // initialize the app
  console.log("A Force app has been loaded, namespace: "
    +app.namespace);
})(
  'firesite', // website app namespace
  'https://9r3i.github.io/force-firesite', // host of ForceFiresite
  'website-config', // from configuration section
  'force-script' // script tag where to store the force.js script
);
```
For more detail see [here](https://github.com/9r3i/force-website)


# Data Setup
Different from ForceWebsite, Firesite using Firebase ```data.driver``` and ```data.config```, for example:
```json
{
  "data": {
    "host": "<firebase_app_namespace>.firebaseapp.com",
    "base": "<database_name>",
    "driver": "Firebase",
    "config": {
      "apiKey": "firebase_app_key",
      "databaseURL": "<firebase_app_database_url>",
      "storageBucket": "gs://<firebase_app_namespace>.appspot.com",
      "authDomain": "<firebase_app_namespace>.firebaseapp.com",
      "projectId": "<firebase_app_namespace>",
      "messagingSenderId": "<firebase_app_messaging_id>",
      "appId": "<firebase_app_id>",
      "measurementId": "<firebase_app_measurement_id>"
    }
  },
}
```
For more detail see [here](https://github.com/9r3i/force-website) and [here](https://github.com/9r3i/force-sample)



# Closing
That's all there is to it. Alhamdulillaah...





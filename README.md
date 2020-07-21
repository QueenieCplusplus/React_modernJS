# React_modernJS
useEffect, promise, forEach

# ES5 & ES6, ES7

ECMAScript 5 簡稱 ES5，為 JS 語言規範。React Native 採用 JS Compiler Babel 轉換 JS 及 JSX，
將新語法轉換為相容（向下相容於） ES5，因此我們可以調整語言規範向上升級為 ES6 也無妨。


# useEffect

      import React, { useEffect } from 'react';

        useEffect(() => {
        
          async function methodCall() {
            const digest = await Crypto.digestStringAsync(
              Crypto.CryptoDigestAlgorithm.SHA256,
              ''
            );
            console.log('Digest: ', digest);
          }
          
          methodCall()
          
        }, []
        
        );


// requestPermission for camera 


            useEffect(() => {
                (async () => {
                  const { status } = await Camera.requestPermissionsAsync();
                  setHasPermission(status === 'granted');
                })();
              }, []);


// requestPermission for geolocation

        useEffect(() => {
        
          (async () => {
            let { status } = await Location.requestPermissionsAsync();
            if (status !== 'granted') {
              setErrorMsg('Permission to access location was denied');
            }

            let location = await Location.getCurrentPositionAsync({});
            setLocation(location);
          })
          
          ();
          
        });


# Promise


   to be continued...


# forEach

   to be continued...
   
# async

       state = {
            result: null,
        };

        pressHandler = async () => {
        
          let result = await WebBrowser.openBrowserAsync('https://www.google.com/');
          this.setState({ result });
          
        };

   
# useState

    import React, { useState, useEffect } from 'react';
  
 //camera
 
    const [hasPermission, setHasPermission] = useState(null);
    const [type, setType] = useState(Camera.Constants.Type.back);
    
 //map
 
     const [location, setLocation] = useState(null);
     const [errorMsg, setErrorMsg] = useState(null); 



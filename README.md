# React_modernJS
useEffect, promise, forEach


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



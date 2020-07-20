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


// requestPermission example


            useEffect(() => {
                (async () => {
                  const { status } = await Camera.requestPermissionsAsync();
                  setHasPermission(status === 'granted');
                })();
              }, []);




# Promise


   to be continued...


# forEach

   to be continued...
   
   
# useState

    import React, { useState, useEffect } from 'react';
  
    const [hasPermission, setHasPermission] = useState(null);
    const [type, setType] = useState(Camera.Constants.Type.back);


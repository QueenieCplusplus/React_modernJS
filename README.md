# React_modernJS
useEffect, promise, forEach


# useEffect

      import React, { useEffect } from 'react';

      export default function App() {
      

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


       return (
       
         <View>
           <Text></Text>
         </View>
       );
      

    }

# React_modernJS
useEffect, promise, forEach

# ES5 & ES6, ES7

ECMAScript 5 簡稱 ES5，為 JS 語言規範。React Native 採用 JS Compiler Babel 轉換 JS 及 JSX，
將新語法轉換為相容（向下相容於） ES5，因此我們可以調整語言規範向上升級為 ES6 也無妨。

* 變數宣告

以往語言版本使用 var，新版本開始劃分 let 和 const ， let 可以重新賦值，const 不可，且 let 僅僅能在宣告在同一程式區塊（local）。

* 預設參數

        //為函式指定預設參數
        
        let userChecker = (name = "plz enter name" ) => {
        
              console.log("welcome," + name + ".")
        
        };
        
        userCheck("Eric"); // welcome, Eric.
        
        userChecker(); // welcom,plz enter name.
        
* 字串插值

        //ES5
        
        const PKQ = 'katesreact2020'
        var url = 'https://github.com/' + PKQ
        
            
        //ES6+
        
        const PKQ = 'katesreact2020'
        let url = 'https://github.com/${PKQ}'
        
        
* 胖箭頭 => 函式與綁定 bind(this)

舊版本，常常需要 bind 函式，讓內容符合預期，尤其是回呼函式。
新版本，不用手動綁定，會自動綁定。

         //ES5

         var callbackfn = function(val){
            //...
         }.bind(this);

         //ES6 +

         let callbackfn(val){

         };

         //alternative

         let callbackfn = (val) =>{

         };


* 模組注入方式
      
      (略)

* 函數簡寫

      (略)


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



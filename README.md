# React_modernJS
useEffect, promise, forEach, map, async, useState & ES5

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
        
        
* 引用透明

  能直接將函式呼叫取代為回傳值（換句話說，直接用回傳值取代整個呼叫）並且不改變程式行為的能力，稱為引用透明。
  
  
        // 郵件範例中，emailBody 即為引用透明。
        
        sendMail(getUser().toGreet(), emailBody)
 
  
  
        // 回傳值（賦值）的引用透明函數範例

        (()=>3000)(); // 回傳 3000
        
        
        
        // 吃葡萄吐葡萄
        
        ((x)=>x)(1000);// 回傳 1000
        
        
        
        // 三倍卷範例
        
        ((1000)=> 3000)()
        
        
        
        // 三倍卷複雜運算範例
        
         /*a為民眾帶領三倍卷交付的現金金額 ; b 為國家政策優惠的倍數
         */
        
        ((a)=>a)(1000) * ((b)=>b)(3); // 回傳3000
        
        
        
* 字串插值

        //ES5
        
        const PKQ = 'katesreact2020'
        var url = 'https://github.com/' + PKQ;
        
            
        //ES6+
        
        const PKQ = 'katesreact2020'
        let url = 'https://github.com/${PKQ}';
        
        
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


# Promise (像是函子之類的高階函式結構)

  Promise 是一種物件，用來表示某事件必然發生，在尚未有 Promise 的時代前，開發者需要手動處理回傳成功或失敗的函數，
  然而有賴於 Promise 發明之後，此 API 提供非同步處理動作。
  
  Promise 的優勢能讓我們輕易的組合函數，回調 (callback) 迫使我們在函式中寫死函式名稱（或是函式字面值)，然後以函式
  的額外參數形式去傳遞。
  
  Promise 幫助我們將如上述的值通通串聯起來，我們有值被包覆在 promise 裡面，然後 then 等待（倘若需要時）並解開它，
  方才將這個值作為參數傳遞給一個 promise 或函式。
  
       // 可用 then 串連回呼函式，避免掉入回呼地獄的陷阱。
       
       updateToAPI().then().then().then()...
       
       // 範例
       
       function successor(res){
       
       }
       
       function errorHandler(err){
       
       }
       
       updateToAPI().then(successor, errorHandler)
       
       // 其他範例
       
       updateToAPI(res=>anotherInterface(res)).
         then(callback=>successor(callback)).
         catch(errorHandler)
         
         
Promise 四步驟：
   
   (1) new Promise || Promise.resolve
   
   (2) 放置一個值或是非同步的產生值的程序到 Promise 裡。
   
   (3) 當計時器或是非同步函式有結果後，這個值，會被 resolve 設置。
   
   (4) 值會被包在 Promise 裡面返回，如同吐司從烤箱中取出，無論途中開關幾度或是加入何種醬料。
   
   Promise 此建構函數擁有兩個回調函式：
   
   * resolve
   
   * reject
   
使用 then 的注意事項：
   
   then 可以接受兩個 promise 或是函式，一是完成時使用，一是拒絕時會用。
   雖然通常顯示一個，完成時使用。
   
     .then(fulfilment, rejection)
     
    
其他函式的用法：
   
   reject 函式能創造出一個被拒絕的 promise 物件，而且有個 .catch() 函式能捕捉錯誤（但也不會全部捕捉），
   .all() 函式則能在所有 promise 完成時回傳， .race() 函式能在第一個 promise 完成時回傳。
   
慎重叮嚀：

   圍繞著 Promise API 的錯誤處理及初始建置有許多變種，會是相當刁鑽的體驗。

# forEach loop

  遍歷自己。
  
      // 範例
    
    let K_Array = [];
    
    [500, 200, 100, 50, 10, 5].forEach(ele=>{
    
         K_Array.push(ele * 2)
    });
  
 
# map

  在陣列上套用函式創造出新陣列。
  
  
    // 範例
    
    let 3timesArray =[1000, 500, 200, 100].map(ele=>{
    
           return ele * 3;
    });
    
    console.log(3timesArray);//[3000, 1500, 600, 300]   
   
# reduce

  基於陣列給出新值，難度比其他 forloop 高，但對於處理聚合的值效果良好，
  倘若遍歷的值型別不太常見，那就特別適合使用 reduce()。
  
  
   
# every, filter, find, some

           to be continued...
   
   
# for of, do...while

  for...of 會比 for...in 安全，因為 fo...in 不保證順序，JS 的 for of 如同其他語言的 for in。 
  
  do...while 基本上與 while 相同，然而停止條件是 while(false) do 只會進行一次。
  
      // do...while
    
      const i = 0;
      let k_memory = [];
      
     do{
     
         k_memory.push(music[i])
         i ++;
      
      }while( i <  music.count());
    
    
# async/ await

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


# Maybe 型別

           to be continued...



# Either 型別

           to be continued...
   
   

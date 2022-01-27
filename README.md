# v2 depolys on railway


<details>
    <summary>cloudflare workers deployment</summary>

 # 单反代
    
```js
addEventListener(
    "fetch",event => {
    let url=new URL(event.request.url);
    url.hostname="xxx.up.railway.app";
    let request=new Request(url,event.request);
    event. respondWith(
      fetch(request)
    )
  }
)
```
    
    
# 双反代
    
```js   
const SingleDay = 'xxx.up.railway.app'
const DoubleDay = 'xxx.up.railway.app'
addEventListener(
    "fetch",event => {

        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }

        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
    
</details>

      
    

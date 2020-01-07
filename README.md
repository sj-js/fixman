# fixman
[![Build Status](https://travis-ci.org/sj-js/fixman.svg?branch=master)](https://travis-ci.org/sj-js/fixman)
[![All Download](https://img.shields.io/github/downloads/sj-js/fixman/total.svg)](https://github.com/sj-js/fixman/releases)
[![Release](https://img.shields.io/github/release/sj-js/fixman.svg)](https://github.com/sj-js/fixman/releases)
[![License](https://img.shields.io/github/license/sj-js/fixman.svg)](https://github.com/sj-js/fixman/releases)

- Causes the Element to be dragged around the screen without being obscured by scrolling
- https://github.com/sj-js/fixman
    
      
        
## Index
*@* **order** *@*
```
- fixman
- Event
- Example
```


## 1. Getting Started

### 1-1. How to use

1. Load library and new instance
    ```html
    <script src="https://cdn.jsdelivr.net/gh/sj-js/crossman/dist/js/crossman.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/sj-js/fixman/dist/js/fixman.js"></script>
    <script>
         var fixman = new FixMan().detect();
    </script>
    ```  
    OR in ES6+
    ```js
    const fixman = require('@sj-js/fixman');
    ```
   
2. Set `data-fixed` to target element   
   ```html
   <div data-fixed>Hello</div>
   ```
   
3. Run `detect()` then, When Page is Loaded, detect and apply elements with a `data-fixed` attribute    
   ```js
   fixman.detect();
   ```



### 1-2. Simple Example
- For convenience, the following code, which loads and creates a Library in the example, is omitted.
    ```html
    <script src="https://cdn.jsdelivr.net/gh/sj-js/crossman/dist/js/crossman.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/sj-js/fixman/dist/js/fixman.js"></script>
    <script>
         var fixman = new FixMan().detect();
    </script>
    ```
  
    *@* *+prefix* *x* *@* 
    ```html
    <script src="../crossman/crossman.js"></script>
    <script src="../fixman/fixman.js"></script>
    <script>
         var fixman = new FixMan().detect();
    </script>
    ```    

##### Sample A
- Example)
    *@* *!* *@*
    ```html
    <style>
        .test1 { display:block; height:50px; border:2px solid black; }
        html { scroll-behavior: smooth; }
    </style>
    <body>
        <div class="test1">Hello Top</div>
        <br/><br/>
        
        <div class="test1" style="width:500px; background:#FFFFFF;" data-fixed>
            <span style="font-size:30px">안녕?</span>
            <input type="text" value="Some Text">
            <button onclick="alert('Testing');">🔎</button>
            <button onclick="window.scrollTo({top:0, behavior:'smooth'});">🔝</button>
        </div>
        <br/><br/><br/>
   
        <div class="test1" style="width:250px; background:pink;">Hello?</div><br/><br/><br/><br/>
        <div class="test1" style="width:200px; background:skyblue;">Annyeong?</div><br/><br/><br/><br/><br/>
        <div class="test1" style="width:300px; background:gold;">Konnichiwa? and Nihao? or Hola?</div><br/><br/><br/><br/><br/><br/>
    </body>
    ``` 

##### Sample B
- Example)
    *@* *!* *@*
    ```html
    <style>
        .test1 { display:block; vertical-align:top; width:350px; height:50px; border:2px solid black; }
        .test2 { display:inline-block; vertical-align:top; width:25px; height:25px; border:2px solid black; }
        html { scroll-behavior: smooth; }
    </style>
    <body>
        <div class="test1" style="background:#FFFFFF;">
            <div class="test2">1</div>
            <div class="test2" style="background:#EEE;" data-fixed>2</div>
            <div class="test2">3</div>
        </div>
        <br/><br/><br/>     
        <div class="test1" style="width:250px; background:pink;">
            <div class="test2" style="background:#BBB;" data-fixed>1</div>
            <div class="test2">2</div>
            <div class="test2">3</div>     
        </div>
        <br/><br/><br/><br/>        
        <div class="test1" style="display:inline-block; width:100px; background:skyblue;">
            <div class="test2">1</div>
            <div class="test2">2</div>
            <div class="test2" style="background:#999;" data-fixed>3</div>
        </div>
        <div class="test1" style="display:inline-block; width:100px; background:skyblue;">
            <div class="test2">가</div>
            <div class="test2">나</div>
            <div class="test2" style="background:#888;" data-fixed>다</div>
        </div>
        <div class="test1" style="display:inline-block; width:100px; background:skyblue;" data-fixed>
            함께 갑시다
        </div> 
        <br/><br/><br/><br/><br/>   
        <div class="test1" style="width:300px; background:gold;">
             <div class="test2">1</div>
             <div class="test2">2</div>
             <div class="test2" style="background:#000;" data-fixed>3</div>
             <div class="test2" style="background:#333;" data-fixed>4</div>
             <div class="test2" style="background:#777;" data-fixed>5</div>
        </div>
        <br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>
        <br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>
    </body>
    ``` 
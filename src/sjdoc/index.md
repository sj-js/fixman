# FixMan
## 📌
[![Build Status](https://travis-ci.org/sj-js/fixman.svg?branch=master)](https://travis-ci.org/sj-js/fixman)
[![All Download](https://img.shields.io/github/downloads/sj-js/fixman/total.svg)](https://github.com/sj-js/fixman/releases)
[![Release](https://img.shields.io/github/release/sj-js/fixman.svg)](https://github.com/sj-js/fixman/releases)
[![License](https://img.shields.io/github/license/sj-js/fixman.svg)](https://github.com/sj-js/fixman/releases)

- Causes the Element to be dragged around the screen without being obscured by scrolling
- ✨ Source: https://github.com/sj-js/fixman
- ✨ Document: https://sj-js.github.io/sj-js/fixman
    
      
        
## Index
*@* **order** *@*
```
- FixMan
- Event
- Example
```



## 1. Getting Started

### 1-1. How to load?
- Browser
    ```html
    <script src="https://cdn.jsdelivr.net/npm/@sj-js/crossman/dist/js/crossman.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@sj-js/fixman/dist/js/fixman.min.js"></script>
    <script>
         var fixman = new FixMan();
    </script>
    ```  
    *@* *+prefix* *x* *@* 
    ```html
    <script src="../crossman/crossman.js"></script>
    <script src="../fixman/fixman.js"></script>
    <script>
        var fixman = new FixMan();
    </script>
    ```  
- ES6+
    ```bash
    npm i @sj-js/fixman
    ```
    ```js
    const FixMan = require('@sj-js/fixman');
    const fixman = new FixMan();
    ```
  
   

### 1-2. Simple Example
For convenience, 1-1 code, which loads and creates a Library in the example, is omitted.

### Example - fix top 
1. Set `data-fixed` to target element   
   ```html
   <div data-fixed>Hello</div>
   ```
   
2. Run `detect()` then, When Page is Loaded, detect and apply elements with a `data-fixed` attribute    
   ```js
   fixman.detect();
   ```
3. 👨‍💻
    *@* *!* *@*
    ```html
    <style>
        .test1 { display:block; height:50px; border:2px solid black; margin-bottom:200px; }
    </style>
    <script>
        fixman.detect();
    </script>
    <body>
        <div class="test1">Please scroll down.</div>
        <div class="test1" style="width:500px; background:#FFFFFF;" data-fixed>
            <span style="font-size:30px">안녕?</span>
            <input type="text" value="Some Text">
            <button onclick="alert('Testing');">🔎</button>
            <button onclick="window.scrollTo({top:0, behavior:'smooth'});">🔝</button>
        </div>
        <div class="test1" style="width:250px; background:pink;">Hello?</div>
        <div class="test1" style="width:200px; background:skyblue;">Annyeong?</div>
        <div class="test1" style="width:300px; background:gold;">Konnichiwa? and Nihao? or Hola?</div>
    </body>
    ``` 

### Example - fix multiple
- 👨‍💻
    *@* *!* *@*
    ```html
    <style>
        .test1 { display:block; vertical-align:top; width:350px; height:50px; border:2px solid black; margin-bottom:200px; }
        .test2 { display:inline-block; vertical-align:top; width:25px; height:25px; border:2px solid black; }
    </style>
    <script>
        fixman.detect();
    </script>
    <body>
        <div class="test1">Please scroll down.</div>
        <div class="test1" style="background:#FFFFFF;">
            <div class="test2">1</div>
            <div class="test2" style="background:#EEE;" data-fixed>2</div>
            <div class="test2">3</div>
        </div>
        <div class="test1" style="width:250px; background:pink;">
            <div class="test2" style="background:#BBB;" data-fixed>1</div>
            <div class="test2">2</div>
            <div class="test2">3</div>     
        </div>
        <div class="test1">Please scroll down.</div>
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
        <div class="test1">Please scroll down.</div> 
        <div class="test1" style="width:300px; background:gold;">
             <div class="test2">1</div>
             <div class="test2">2</div>
             <div class="test2" style="background:#000;" data-fixed>3</div>
             <div class="test2" style="background:#333;" data-fixed>4</div>
             <div class="test2" style="background:#777;" data-fixed>5</div>
        </div>
        <div class="test1">Please scroll Up.</div> 
    </body>
    ``` 

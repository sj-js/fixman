# FixMan
## 📌
[![Build Status](https://travis-ci.org/sj-js/fixman.svg?branch=master)](https://travis-ci.org/sj-js/fixman)
[![All Download](https://img.shields.io/github/downloads/sj-js/fixman/total.svg)](https://github.com/sj-js/fixman/releases)
[![Release](https://img.shields.io/github/release/sj-js/fixman.svg)](https://github.com/sj-js/fixman/releases)
[![License](https://img.shields.io/github/license/sj-js/fixman.svg)](https://github.com/sj-js/fixman/releases)

- Causes the Element to be dragged around the screen without being obscured by scrolling
- ✨ Source: https://github.com/sj-js/fixman
- ✨ Document: https://sj-js.github.io/sj-js/fixman
    
        

## 1. Getting Started

0. Load
    - Browser
        ```html
        <script src="https://cdn.jsdelivr.net/npm/@sj-js/crossman/dist/js/crossman.min.js"></script>
        <script src="https://cdn.jsdelivr.net/npm/@sj-js/fixman/dist/js/fixman.min.js"></script>
        <script>
             var fixman = new FixMan();
        </script>
        ```  
    - ES6+
        ```js
        const fixman = require('@sj-js/fixman');
        ```
   
1. Set `data-fixed` to target element   
   ```html
   <div data-fixed>Hello</div>
   ```
   
2. Run `detect()` then, When Page is Loaded, detect and apply elements with a `data-fixed` attribute    
   ```js
   fixman.detect();
   ```

3. Simple Example
    ```html
    <!DOCTYPE html>
    <HTML>
        <head>
            <script src="https://cdn.jsdelivr.net/npm/@sj-js/crossman/dist/js/crossman.min.js"></script>
            <script src="https://cdn.jsdelivr.net/npm/@sj-js/fixman/dist/js/fixman.min.js"></script>
            <script>
                var fixman = new FixMan();
            </script>
            <script>
                fixman.detect();
            </script>
        </head>
    
        <style>
            .test1 { display:block; height:50px; border:2px solid black; margin-bottom:200px; }
        </style>
    
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
            <div class="test1" style="width:500px; background:forestgreen;">How are you?</div>
            <div class="test1" style="width:800px; background:chocolate;">Como esta?</div>
        </body>
    </HTML>
    ``` 
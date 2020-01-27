# Event
Scroll에 따라서 대상 Element를 기준으로 Event를 발생시킬 수 있습니다.   

#### ※ 표
 종류 | 설명
------|-----
FixMan.EVENT_AFTERDETECT | detect가 완료된 후
FixMan.EVENT_DETACH | Scroll-Down으로 붙었던 Element가 다시 Scroll-Up에 의해 떨어질 때  
FixMan.EVENT_ANIMATIONBYOBJECTHEIGHT | Scroll시 발생 - (화면과 대상 Original Element와의 데이터를 제공)  
FixMan.EVENT_ANIMATIONSTARTBYOBJECTHEIGHT | Scroll-Down시 Original Element의 영역이 가려지기 시작할 때
FixMan.EVENT_ANIMATIONDOINGBYOBJECTHEIGHT | Scroll-Down시 Original Element의 영역 가려지기 시작할 때부터 완전히 가려질 때까지 
FixMan.EVENT_ANIMATIONENDBYOBJECTHEIGHT | Scroll-Down시 Original Element의 영역이 완전히 가려질 때

*@* *+prefix* *x* *@* 
```html
<script src="../crossman/crossman.js"></script>
<script src="../fixman/fixman.js"></script>
<script>
     var fixman = new FixMan();
</script>
```




## Event - Animation
- example)
    *@* *!* *@*
    ```html
    <style>
        .title-context {
            dislpay:block; width:100%;
            color:#fff; text-align:center; font-size: 70px; font-weight: bold; transition-duration: 0.5s;
        }
        .title-text {
            color:#fff; text-align:center; font-size: 70px;
        }
        #logo-clone { 
            position: initial; transform: initial; display: inline-block; font-size: 25px; transition: 1s;
            border: 3px solid yellow; border-radius: 25px; background: #b9b63b; opacity: 0; cursor: pointer;
        }
        .test1 { 
            display:block; vertical-align:top; width:350px; height:200px; border:2px solid black; border-radius:20px;
            margin-bottom: 200px; 
        }
    </style>

    <body>
        <div id="title-context" class="title-context" data-fixed>
            <span id="title-text" class="title-text">
                Jelly
                <span id="title-logo" style="vertical-align:bottom; border:0px">🥝</span>
            </span>
        </div>
        <div class="test1" style="background:pink;">Hello?</div>
        <div class="test1" style="background:skyblue;">Annyeong?</div>
        <div class="test1" style="background:gold;">Konnichiwa? and Nihao? or Hola?</div>
        <div class="test1" style="background:gold;">안녕? 좋은하루!? :D</div>
    </body>

    <script>
        fixman.detect();
        fixman.addEventListener('title-context', FixMan.EVENT_ANIMATIONSTARTBYOBJECTHEIGHT, function(object){
            var logoElement = document.getElementById('title-logo');
            var clonedLogo = logoElement.cloneNode(true);
            clonedLogo.setAttribute('id', 'logo-clone');
            clonedLogo.addEventListener('click', function(){
                window.scrollTo({top:0, behavior:'smooth'}); 
            });
            document.body.appendChild(clonedLogo);
            setTimeout(function(){
                var clonedLogo = document.getElementById('logo-clone');
                if (clonedLogo)
                    clonedLogo.style.cssText = 'position:fixed; left:0px; top:0px; border-radius:50px 50px 50px 50px; opacity:1; fontSize:35px;';
            }, 1);
        });
        fixman.addEventListener('title-context', FixMan.EVENT_ANIMATIONBYOBJECTHEIGHT, function(data){
            var object = data.object;
            var rate = data.rateLimit;
            var rateReverse = data.rateLimitReverse;
            object.style.transform = 'translateX('+ -(window.innerWidth/2 *rate) +'px) translateY('+ -(data.fixableObjectHeight *rate) +'px) scaleY('+ rateReverse +')';
        });
        fixman.addEventListener('title-context', FixMan.EVENT_DETACH, function(object){
            var clonedLogo = document.getElementById('logo-clone');
            if (clonedLogo){
                clonedLogo.style.borderRadius = '45px';
                clonedLogo.style.opacity = '0';
                setTimeout(function(){
                    var clonedLogo = document.getElementById('logo-clone');
                    if (!object.statusFixed && clonedLogo && clonedLogo.parentNode)
                        clonedLogo.parentNode.removeChild(clonedLogo);
                }, 1000);
            }       
        });
    </script>
    ```



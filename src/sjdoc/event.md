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

#### ※ 자동적용
- 편의를 위해서 예제에서는 다음 코드가 생략되어 있습니다.
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
            position: initial; transform: initial; display: inline-block; font-size: 1px; transition: 1s;
            border: 3px solid yellow; border-radius: 25px; background: #b9b63b; opacity: 0; cursor: pointer;
        }
        .test1 { 
            display:block; vertical-align:top; width:350px; height:200px; border:2px solid black; border-radius:20px; 
        }
    </style>

    <body>
        <div id="title-context" class="title-context" data-fixed>
            <span id="title-text" class="title-text">
                Jelly
                <span id="title-logo" style="vertical-align:bottom; border:0px">🥝</span>
            </span>
        </div>
        <div class="test1" style="background:pink;">Hello?</div><br/><br/><br/><br/>
        <div class="test1" style="background:skyblue;">Annyeong?</div><br/><br/><br/><br/><br/>
        <div class="test1" style="background:gold;">Konnichiwa? and Nihao? or Hola?</div><br/><br/><br/><br/><br/><br/>
        <div class="test1" style="background:gold;">안녕? 좋은하루!? :D</div><br/><br/><br/><br/><br/>
    </body>

    <script>
        fixman.addEventListener('title-context', FixMan.EVENT_ANIMATIONSTARTBYOBJECTHEIGHT, function(object){
            cloneEl('title-logo', true).attr('id', 'logo-clone').removeClass('title-text').appendTo(document.body).addEventListener('click', function(){
                window.scrollTo({top:0, behavior:'smooth'}); 
            }); 
            setTimeout(function(){
                getEl('logo-clone').exists(function(it){
                    it.style('position:fixed; left:0px; top:0px;').setStyle('borderRadius', '50px 50px 50px 50px').setStyle('opacity', '1').setStyle('fontSize', '35px');
                });
            }, 1);
        });
        fixman.addEventListener('title-context', FixMan.EVENT_ANIMATIONBYOBJECTHEIGHT, function(data){
            var object = data.object;
            var rate = data.rateLimit;
            var rateReverse = data.rateLimitReverse;
            object.style.transform = 'translateX('+ -(window.innerWidth/2 *rate) +'px) translateY('+ -(data.fixableObjectHeight *rate) +'px) scaleY('+ rateReverse +')';
        });
        fixman.addEventListener('title-context', FixMan.EVENT_DETACH, function(object){
            getEl('logo-clone').exists(function(it){
                it.setStyle('borderRadius', '45px').setStyle('opacity', '0');
                setTimeout(function(){
                    if (!object.statusFixed && it.exists() && it.existsParent())
                        it.removeFromParent();
                }, 1000);
            });
        });  
    </script>
    ```



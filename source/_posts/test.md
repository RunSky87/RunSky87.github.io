---
title: test
date: 2021-03-12 10:38:12
tags:
---

[美化教程](https://zhuanlan.zhihu.com/p/69211731)

 
```javascript
var a = 12321
```
```javascript
var a = 12321
```
```C
var a = 12321
```
<!-- more -->

```C#
var a = 12321
using System;
using System.ComponentModel;

namespace EM
{
    public class SysUserEM
    {
        [Description("用户ID"), Category("系统-用户表"), DisplayName("用户ID")]
        public string UserId { get; set; }

        [Description("名称"), Category("系统-用户表"), DisplayName("名称")]
        public string UserName { get; set; }

        [Description("密码"), Category("系统-用户表"), DisplayName("密码")]
        public string SPwd { get; set; }

        [Description("手机号"), Category("系统-用户表"), DisplayName("手机号")]
        public string SMobile { get; set; }

        [Description("Email"), Category("系统-用户表"), DisplayName("Email")]
        public string SEmail { get; set; }

        [Description("状态"), Category("系统-用户表"), DisplayName("状态")]
        public string UserStatus { get; set; }

        [Description("创建日期"), Category("系统-用户表"), DisplayName("创建日期")]
        public DateTime DTime { get; set; }

        [Description("备注"), Category("系统-用户表"), DisplayName("备注")]
        public string SNote { get; set; }

    }
}

```
``` html /blog/index.html Tyrion Yu tyrionyu-blog
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
</body>
</html>
```

<div id="binft"></div>
  <script>
    var binft = function (r) {
      function t() {
        return b[Math.floor(Math.random() * b.length)]
      }  
      function e() {
        return String.fromCharCode(94 * Math.random() + 33)
      }
      function n(r) {
        for (var n = document.createDocumentFragment(), i = 0; r > i; i++) {
          var l = document.createElement("span");
          l.textContent = e(), l.style.color = t(), n.appendChild(l)
        }
        return n
      }
      function i() {
        var t = o[c.skillI];
        c.step ? c.step-- : (c.step = g, c.prefixP < l.length ? (c.prefixP >= 0 && (c.text += l[c.prefixP]), c.prefixP++) : "forward" === c.direction ? c.skillP < t.length ? (c.text += t[c.skillP], c.skillP++) : c.delay ? c.delay-- : (c.direction = "backward", c.delay = a) : c.skillP > 0 ? (c.text = c.text.slice(0, -1), c.skillP--) : (c.skillI = (c.skillI + 1) % o.length, c.direction = "forward")), r.textContent = c.text, r.appendChild(n(c.prefixP < l.length ? Math.min(s, s + c.prefixP) : Math.min(s, t.length - c.skillP))), setTimeout(i, d)
      }
      var l = "",
      o = ["青青陵上柏，磊磊涧中石。", "人生天地间，忽如远行客。","斗酒相娱乐，聊厚不为薄。", "驱车策驽马，游戏宛与洛。","洛中何郁郁，冠带自相索。","长衢罗夹巷，王侯多第宅。","两宫遥相望，双阙百余尺。","极宴娱心意，戚戚何所迫？"].map(function (r) {
      return r + ""
      }),
      a = 2,
      g = 1,
      s = 5,
      d = 75,
      b = ["rgb(110,64,170)", "rgb(150,61,179)", "rgb(191,60,175)", "rgb(228,65,157)", "rgb(254,75,131)", "rgb(255,94,99)", "rgb(255,120,71)", "rgb(251,150,51)", "rgb(226,183,47)", "rgb(198,214,60)", "rgb(175,240,91)", "rgb(127,246,88)", "rgb(82,246,103)", "rgb(48,239,130)", "rgb(29,223,163)", "rgb(26,199,194)", "rgb(35,171,216)", "rgb(54,140,225)", "rgb(76,110,219)", "rgb(96,84,200)"],
      c = {
        text: "",
        prefixP: -s,
        skillI: 0,
        skillP: 0,
        direction: "forward",
        delay: a,
        step: g
      };
      i()
      };
      binft(document.getElementById('binft'));
  </script>

<iframe frameborder="no"  border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=1355197518&auto=1&height=66"></iframe>


<script>
<!--浏览器搞笑标题-->
 var OriginTitle = document.title;
 var titleTime;
 document.addEventListener('visibilitychange', function () {
     if (document.hidden) {
         $('[rel="icon"]').attr('href', "/img/trhx2.png");
         document.title = 'ヽ(●-`Д´-)ノ你丑你就走！';
         clearTimeout(titleTime);
     }
     else {
         $('[rel="icon"]').attr('href', "/img/trhx2.png");
         document.title = 'ヾ(Ő∀Ő3)ノ你帅就回来！' + OriginTitle;
         titleTime = setTimeout(function () {
             document.title = OriginTitle;
         }, 2000);
     }
 });
</script>

<script type="text/javascript"
color="220,220,220" opacity='0.7' zIndex="-2" count="200" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js">
</script>
<script>
/*样式一*/
(function($){
    $.fn.snow = function(options){
    var $flake = $('<div id="snowbox" />').css({'position': 'absolute','z-index':'9999', 'top': '-50px'}).html('&#10052;'),
    documentHeight  = $(document).height(),
    documentWidth   = $(document).width(),
    defaults = {
        minSize     : 10,
        maxSize     : 20,
        newOn       : 1000,
        flakeColor  : "#AFDAEF" /* 此处可以定义雪花颜色，若要白色可以改为#FFFFFF */
    },
    options = $.extend({}, defaults, options);
    var interval= setInterval( function(){
    var startPositionLeft = Math.random() * documentWidth - 100,
    startOpacity = 0.5 + Math.random(),
    sizeFlake = options.minSize + Math.random() * options.maxSize,
    endPositionTop = documentHeight - 200,
    endPositionLeft = startPositionLeft - 500 + Math.random() * 500,
    durationFall = documentHeight * 10 + Math.random() * 5000;
    $flake.clone().appendTo('body').css({
        left: startPositionLeft,
        opacity: startOpacity,
        'font-size': sizeFlake,
        color: options.flakeColor
    }).animate({
        top: endPositionTop,
        left: endPositionLeft,
        opacity: 0.2
    },durationFall,'linear',function(){
        $(this).remove()
    });
    }, options.newOn);
    };
})(jQuery);
$(function(){
    $.fn.snow({ 
        minSize: 5, /* 定义雪花最小尺寸 */
        maxSize: 50,/* 定义雪花最大尺寸 */
        newOn: 300  /* 定义密集程度，数字越小越密集 */
    });
});
</script>

<script>

// 鼠标样式
document.querySelector("body").style.cursor = 'url(https://blog.shanamaid.top/css/images/icon.png),default';

!function(e,t,a){function n(){c(".heart{width: 10px;height: 10px;position: fixed;background: #f00;transform: rotate(45deg);-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);}.heart:after,.heart:before{content: '';width: inherit;height: inherit;background: inherit;border-radius: 50%;-webkit-border-radius: 500%;-moz-border-radius: 50%;position: fixed;}.heart:after{top: -5px;}.heart:before{left: -5px;}"),o(),r()}function r(){for(var e=0;e<d.length;e++)d[e].alpha<=0?(t.body.removeChild(d[e].el),d.splice(e,1)):(d[e].y--,d[e].scale+=.004,d[e].alpha-=.013,d[e].el.style.cssText="left:"+d[e].x+"px;top:"+d[e].y+"px;opacity:"+d[e].alpha+";transform:scale("+d[e].scale+","+d[e].scale+") rotate(45deg);background:"+d[e].color+";z-index:99999");requestAnimationFrame(r)}function o(){var t="function"==typeof e.onclick&&e.onclick;e.onclick=function(e){t&&t(),i(e)}}function i(e){var a=t.createElement("div");a.className="heart",d.push({el:a,x:e.clientX-5,y:e.clientY-5,scale:1,alpha:1,color:s()}),t.body.appendChild(a)}function c(e){var a=t.createElement("style");a.type="text/css";try{a.appendChild(t.createTextNode(e))}catch(t){a.styleSheet.cssText=e}t.getElementsByTagName("head")[0].appendChild(a)}function s(){return"rgb("+~~(255*Math.random())+","+~~(255*Math.random())+","+~~(255*Math.random())+")"}var d=[];e.requestAnimationFrame=function(){return e.requestAnimationFrame||e.webkitRequestAnimationFrame||e.mozRequestAnimationFrame||e.oRequestAnimationFrame||e.msRequestAnimationFrame||function(e){setTimeout(e,1e3/60)}}(),n()}(window,document);
</script>

<iframe
  src="https://carbon.now.sh/embed?bg=rgba%28171%2C184%2C195%2C0%29&t=seti&wt=none&l=auto&ds=true&dsyoff=16px&dsblur=14px&wc=true&wa=true&pv=34px&ph=48px&ln=false&fl=1&fm=Hack&fs=13px&lh=148%25&si=false&es=2x&wm=false&code=var%2520spiralOrder%2520%253D%2520function%28matrix%29%2520%257B%250A%2520%2520%2520%2520if%2520%28%21matrix.length%2520%257C%257C%2520%21matrix%255B0%255D.length%29%2520%257B%250A%2520%2520%2520%2520%2520%2520%2520%2520return%2520%255B%255D%253B%250A%2520%2520%2520%2520%257D%250A%2520%2520%2520%2520const%2520rows%2520%253D%2520matrix.length%252C%2520columns%2520%253D%2520matrix%255B0%255D.length%253B%250A%2520%2520%2520%2520const%2520visited%2520%253D%2520new%2520Array%28rows%29.fill%280%29.map%28%28%29%2520%253D%253E%2520new%2520Array%28columns%29.fill%28false%29%29%253B%250A%2520%2520%2520%2520const%2520total%2520%253D%2520rows%2520*%2520columns%253B%250A%2520%2520%2520%2520const%2520order%2520%253D%2520new%2520Array%28total%29.fill%280%29%253B%250A%250A%2520%2520%2520%2520let%2520directionIndex%2520%253D%25200%252C%2520row%2520%253D%25200%252C%2520column%2520%253D%25200%253B%250A%2520%2520%2520%2520const%2520directions%2520%253D%2520%255B%255B0%252C%25201%255D%252C%2520%255B1%252C%25200%255D%252C%2520%255B0%252C%2520-1%255D%252C%2520%255B-1%252C%25200%255D%255D%253B%250A%2520%2520%2520%2520for%2520%28let%2520i%2520%253D%25200%253B%2520i%2520%253C%2520total%253B%2520i%252B%252B%29%2520%257B%2520%250A%2520%2520%2520%2520%2520%2520%2520%2520order%255Bi%255D%2520%253D%2520matrix%255Brow%255D%255Bcolumn%255D%253B%250A%2520%2520%2520%2520%2520%2520%2520%2520visited%255Brow%255D%255Bcolumn%255D%2520%253D%2520true%253B%250A%2520%2520%2520%2520%2520%2520%2520%2520const%2520nextRow%2520%253D%2520row%2520%252B%2520directions%255BdirectionIndex%255D%255B0%255D%252C%2520nextColumn%2520%253D%2520column%2520%252B%2520directions%255BdirectionIndex%255D%255B1%255D%253B%250A%2520%2520%2520%2520%2520%2520%2520%2520if%2520%28%21%280%2520%253C%253D%2520nextRow%2520%2526%2526%2520nextRow%2520%253C%2520rows%2520%2526%2526%25200%2520%253C%253D%2520nextColumn%2520%2526%2526%2520nextColumn%2520%253C%2520columns%2520%2526%2526%2520%21%28visited%255BnextRow%255D%255BnextColumn%255D%29%29%29%2520%257B%250A%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520%2520directionIndex%2520%253D%2520%28directionIndex%2520%252B%25201%29%2520%2525%25204%253B%250A%2520%2520%2520%2520%2520%2520%2520%2520%257D%250A%2520%2520%2520%2520%2520%2520%2520%2520row%2520%252B%253D%2520directions%255BdirectionIndex%255D%255B0%255D%253B%250A%2520%2520%2520%2520%2520%2520%2520%2520column%2520%252B%253D%2520directions%255BdirectionIndex%255D%255B1%255D%253B%250A%2520%2520%2520%2520%257D%250A%2520%2520%2520%2520return%2520order%253B%250A%257D%253B"
  style="width: 1024px; height: 698px; border:0; transform: scale(1); overflow:hidden;"
  sandbox="allow-scripts allow-same-origin">
</iframe>

![https://zhangbaoyuan.oss-cn-shanghai.aliyuncs.com/test/carbon.png?versionId=CAEQIBiBgMC3_7XQwRciIGE1ZjRmY2ZmOTY4NzQ5ODNiMTFkMmQ4ZDc1YTA2YmU2](https://zhangbaoyuan.oss-cn-shanghai.aliyuncs.com/test/carbon.png?versionId=CAEQIBiBgMC3_7XQwRciIGE1ZjRmY2ZmOTY4NzQ5ODNiMTFkMmQ4ZDc1YTA2YmU2)

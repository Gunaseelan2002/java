//Headers

#include <ESP8266WiFi.h>
#include <ESPAsyncWebServer.h>
#include <BlynkSimpleEsp8266.h>
#include <Preferences.h>

// Object Creation

Preferences pref;


// Blynk configuration

#define BLYNK_TEMPLATE_ID "TMPLPbOFmdfy"
#define BLYNK_DEVICE_NAME "NodemcuBlynk"
#define BLYNK_AUTH_TOKEN "3RsCJ4ME8IRkMLMkE334s038A1f1EZbH"

//variables

unsigned long previousMillis = 0;
const long INTERVAL = 6000;

// WiFi credentials

char ssid[] = "WiF-5G";
char pass[] = "12345678";

//Webpage Coding

char main_pass[] PROGMEM = R"=====(
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>SmartHome Security</title>
  <style>
    *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins',sans-serif;
    }
    body{
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background: #23242a;
    }
    .box{
      position: relative;
      width: 380px;
      height: 300px;
      background: #1c1c1c;
      border-radius: 8px;
    }
    .form{
      position: absolute;
      inset: 2px;
      border-radius: 8px;
      background: #282924;
      z-index: 10;
      padding: 50px 40px;
      display: flex;
      flex-direction: column;
    }
    .form h2{
      color: #45f3ff;
      font-weight: 500;
      text-align: center;
      letter-spacing: 0.1em;
    }
    .inputBox{
      position: relative;
      width: 300px;
      margin-top: 35px;
    }
    .inputBox input{
      position: relative;
      width: 100%;
      padding: 20px 10px 10px;
      background: transparent;
      border: none;
      outline: none;
      color: #23242a;
      font-size: 1em;
      letter-spacing: 0.05em;
      z-index: 10;
    }
    .inputBox span{
      position: absolute;
      left: 0;
      padding: 20px 0px 10px;
      font-size: 1em;
      color: #8f8f8f;
      pointer-events: none;
      letter-spacing: 0.05em;
      transition: 0.5s;
    }
    .inputBox input:valid ~ span,
    .inputBox input:focus ~ span{
      color: #45f3ff;
      transform: translateX(0px) translateY(-34px);
      font-size: 0.75em;
    }
    .inputBox i{
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 2px;
      background: #45f3ff;
      border-radius: 4px;
      transition: 0.5s;
      pointer-events: none;
      z-index: 9;
    }
    .inputBox input:valid ~ i,
    .inputBox input:focus ~ i{
      height: 44px;
    }
    .links{
      display: flex;
      justify-content: space-between;
    }
    .links h1{
      margin: 10px 80px 0;
      font-size: 0.73em;
      color: #8f8f8f;
      text-decoration: none;
    }
    .links h1:hover{
      color: #45f3ff;
    }
    input[type="submit"]{
      border: none;
      outline: none;
      background: #45f3ff;
      padding: 11px 25px;
      width: 100%;
      margin-top: 10px;
      border-radius: 4px;
      font-weight: 600;
      cursor: pointer;
    }
    .error-text{
      position: absolute;
      background: #f8d7da;
      padding: 10px;
      border-radius: 5px;
      color: #8b3e46;
      border-radius: 1px solid #f5c6cb;
      display: none;
      margin-bottom: 480px;
      font-weight: bold;
      width: 50%;
    }
  </style>
</head>
<body oncontextmenu="return false;">
  <div class="box">
    <div class="form">
      <h2>Smart Home Security</h2>
      <div class="inputBox">
        <input type="password" required id="pass1">
        <span>Enter Password</span>
        <i></i>
      </div>
      <div class="links">
        <h1>welcome to Smart Home</h1>
      </div>
      <input type="submit" value="Ready to Control" onclick="return passcheck()">
    </div>
  </div>
  <div class="error-text"></div>
  <script>
    const _0x971ad8=_0x23fb;function _0x23fb(_0x22f2eb,_0x1d051e){const _0x12a27e=_0x12a2();return _0x23fb=function(_0x23fbe8,_0x2a0e2e){_0x23fbe8=_0x23fbe8-0x143;let _0x1999d8=_0x12a27e[_0x23fbe8];return _0x1999d8;},_0x23fb(_0x22f2eb,_0x1d051e);}function _0x12a2(){const _0x3b8cd4=['charCodeAt','querySelector','pass1','20073500fMuBdo','3666789GCLeVu','0x32','keyCode','665weWonr','getElementById','213183PtgGfT','6936nlzlBh','replace','440giCJIh','display','335614xnwcVa','ctrlKey','onkeydown','/d9MJhdETkB','3781737OCCWMJ','2hPNwiM','value','shiftKey','location','7573278SyEMnY'];_0x12a2=function(){return _0x3b8cd4;};return _0x12a2();}(function(_0x1fce91,_0x1c3d4a){const _0x485f64=_0x23fb,_0x2ddfe6=_0x1fce91();while(!![]){try{const _0x37aaf5=-parseInt(_0x485f64(0x15a))/0x1+-parseInt(_0x485f64(0x147))/0x2*(-parseInt(_0x485f64(0x146))/0x3)+-parseInt(_0x485f64(0x156))/0x4*(parseInt(_0x485f64(0x153))/0x5)+parseInt(_0x485f64(0x14b))/0x6+-parseInt(_0x485f64(0x150))/0x7+parseInt(_0x485f64(0x158))/0x8*(parseInt(_0x485f64(0x155))/0x9)+-parseInt(_0x485f64(0x14f))/0xa;if(_0x37aaf5===_0x1c3d4a)break;else _0x2ddfe6['push'](_0x2ddfe6['shift']());}catch(_0x475690){_0x2ddfe6['push'](_0x2ddfe6['shift']());}}}(_0x12a2,0xb1c64),document[_0x971ad8(0x144)]=function(_0x2e2deb){const _0x4f994d=_0x971ad8;if(event['keyCode']==0x7b)return![];if(_0x2e2deb[_0x4f994d(0x143)]&&_0x2e2deb[_0x4f994d(0x149)]&&_0x2e2deb['keyCode']=='I'[_0x4f994d(0x14c)](0x0))return![];if(_0x2e2deb[_0x4f994d(0x143)]&&_0x2e2deb[_0x4f994d(0x149)]&&_0x2e2deb['keyCode']=='J'[_0x4f994d(0x14c)](0x0))return![];if(_0x2e2deb[_0x4f994d(0x143)]&&_0x2e2deb[_0x4f994d(0x152)]=='U'['charCodeAt'](0x0))return![];});const errorText=document[_0x971ad8(0x14d)]('.error-text');var Password=_0x971ad8(0x151);function passcheck(){const _0x3a0671=_0x971ad8;if(document['getElementById'](_0x3a0671(0x14e))[_0x3a0671(0x148)]!=Password)return errorText['style'][_0x3a0671(0x159)]='block',errorText['textContent']='ERROR!\x20Password\x20is\x20incorrect',![];document[_0x3a0671(0x154)](_0x3a0671(0x14e))['value']==Password&&window[_0x3a0671(0x14a)][_0x3a0671(0x157)](_0x3a0671(0x145));}
  </script>
</body>
</html>
)=====";

char main_page[] PROGMEM = R"=====(
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>SmartHome</title>
  <style>
    *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins',sans-serif;
    }
    body{
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background: antiquewhite;
    }
    h1{
      position: absolute;
      top: 30px;
      left: 0;
      font-size: 60px;
      letter-spacing: 15px;
      color: #777;
      text-transform: uppercase;
      width: 100%;
      height: 100%;
      text-align: center;
      -webkit-box-reflect: below 1px linear-gradient(transparent,#0004);
      line-height: 0.70em;
      outline: none;
      animation: animate_tube 5s linear infinite;
    }
    @keyframes animate_tube{
      0%,18%,20%,50.1%,60%,65.1%,80%,90.1%,92%{
        color: #777;
        text-shadow: none;
      }
      18.1%,20.1%,30%,50%,60.1%,65%,80.1%,90%,92.1%,100%{
        color: #fff;
        text-shadow: 0 0 10px #03bcf4,
        0 0 20px #03bcf4,
        0 0 40px #03bcf4,
        0 0 80px #03bcf4,
        0 0 160px #03bcf4;
      }
    }
    .container{
      display: flex;
      justify-content: center;
      align-items: center;
      max-width: 1200px;
      flex-wrap: wrap;
      padding: 120px 0;
    }
    .container .card{
      position: relative;
      width: 220px;
      height: 240px;
      box-shadow: inset 5px 5px 5px rgba(0, 0, 0, 0.05),
                  inset -5px -5px 5px rgba(255,255,255,0.5),
                  5px 5px 5px rgba(0,0,0,0.05),
                  -5px -5px 5px rgba(255,255,255,0.5);
      border-radius: 15px;
      margin: 30px;
    }
    .container .card .box{
      position: absolute;
      top: 20px;
      left: 20px;
      right: 20px;
      bottom: 20px;
      background: #ebf5fc;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
      border-radius: 15px;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: 0.5s;
    }
    .container .card:hover .box{
      transform: translateY(-50px);
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
      background: linear-gradient(45deg,#b95ce4,#4f29cd);
    }
    .container .card .box .content{
      padding: 20px;
      text-align: center;
    }
    .container .card .box .content h2{
      position: absolute;
      top: -10px;
      right: 30px;
      font-size: 8em;
      color: rgba(0, 0, 0, 0.02);
      transition: 0.5s;
      pointer-events: none;
    }
    .container .card:hover .box .content h2{
      color: rgba(0, 0, 0, 0.1);
    }
    .container .card .box .content h3{
      font-size: 1.8em;
      color: #777;
      z-index: 1;
      transition: 0.5s;
    }
    .container .card:hover .box .content h3{
      color: #fff;
    }
    .container .card .box .content a{
      position: relative;
      display: inline-block;
      padding: 6px 18px;
      background: #03a9f4;
      margin-top: 13px;
      border-radius: 18px;
      color: #fff;
      text-decoration: none;
      font-weight: 400;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.02);
    }
    .container .card:hover .box .content a{
      background: #ff568f;
    }
  </style>
</head>
<body oncontextmenu="return false;">
  <h1>Smart Home</h1>
  <div class="container">
    <div class="card">
      <div class="box">
        <div class="content">
          <h2>01</h2>
          <h3>Switch 1</h3>
          <a onclick="window.location='http://'+location.hostname+'/HyuTDQHKzc'">ON</a>
          <a onclick="window.location='http://'+location.hostname+'/RPdj1egQuO'">OFF</a>
        </div>
      </div>
    </div>

    <div class="card">
      <div class="box">
        <div class="content">
          <h2>02</h2>
          <h3>Switch 2</h3>
          <a onclick="window.location='http://'+location.hostname+'/TFahz4fluF'">ON</a>
          <a onclick="window.location='http://'+location.hostname+'/bymzqwAXXz'">OFF</a>
        </div>
      </div>
    </div>

    <div class="card">
      <div class="box">
        <div class="content">
          <h2>03</h2>
          <h3>Switch 3</h3>
          <a onclick="window.location='http://'+location.hostname+'/F6tksoIQhT'">ON</a>
          <a onclick="window.location='http://'+location.hostname+'/pub7iMb3K4'">OFF</a>
        </div>
      </div>
    </div>

    <div class="card">
      <div class="box">
        <div class="content">
          <h2>04</h2>
          <h3>Switch 4</h3>
          <a onclick="window.location='http://'+location.hostname+'/zkihjcDEzr'">ON</a>
          <a onclick="window.location='http://'+location.hostname+'/yb0F8C2GGX'">OFF</a>
        </div>
      </div>
    </div>

     <div class="card">
      <div class="box">
        <div class="content">
          <h3>Power Supply</h3>
          <a onclick="alert('Make sure to Shutdown your Home!'),window.location='http://'+location.hostname+'/kehEvTqTLc'">Shutdown</a>
          <a onclick="alert('Make sure to Power on your Home!'),window.location='http://'+location.hostname+'/Q6Y61nKtdn'">Power ON</a>
        </div>
      </div>
    </div>
  </div>
  <script>
    function _0x54a1(_0x1726a4,_0x2c42cf){var _0x49313c=_0x4931();return _0x54a1=function(_0x54a10b,_0x31e09c){_0x54a10b=_0x54a10b-0x8a;var _0x59e525=_0x49313c[_0x54a10b];return _0x59e525;},_0x54a1(_0x1726a4,_0x2c42cf);}var _0x525d4b=_0x54a1;(function(_0x5f4cdc,_0x15d4c9){var _0x2e6981=_0x54a1,_0x933fb4=_0x5f4cdc();while(!![]){try{var _0x5b5dfb=parseInt(_0x2e6981(0x8f))/0x1*(parseInt(_0x2e6981(0x8e))/0x2)+parseInt(_0x2e6981(0x90))/0x3*(-parseInt(_0x2e6981(0x8a))/0x4)+-parseInt(_0x2e6981(0x8d))/0x5+-parseInt(_0x2e6981(0x97))/0x6+parseInt(_0x2e6981(0x95))/0x7+-parseInt(_0x2e6981(0x94))/0x8+parseInt(_0x2e6981(0x91))/0x9;if(_0x5b5dfb===_0x15d4c9)break;else _0x933fb4['push'](_0x933fb4['shift']());}catch(_0x49a3cb){_0x933fb4['push'](_0x933fb4['shift']());}}}(_0x4931,0x6cd21),document[_0x525d4b(0x92)]=function(_0x50dd71){var _0x2dee19=_0x525d4b;if(event[_0x2dee19(0x8b)]==0x7b)return![];if(_0x50dd71[_0x2dee19(0x93)]&&_0x50dd71[_0x2dee19(0x8c)]&&_0x50dd71[_0x2dee19(0x8b)]=='I'[_0x2dee19(0x96)](0x0))return![];if(_0x50dd71[_0x2dee19(0x93)]&&_0x50dd71[_0x2dee19(0x8c)]&&_0x50dd71[_0x2dee19(0x8b)]=='J'[_0x2dee19(0x96)](0x0))return![];if(_0x50dd71['ctrlKey']&&_0x50dd71[_0x2dee19(0x8b)]=='U'[_0x2dee19(0x96)](0x0))return![];});function _0x4931(){var _0x2a9abf=['3820236RjZWAv','charCodeAt','3093378NNrjMU','37736DKHBon','keyCode','shiftKey','1497490yulANB','2OdanoK','697819otmTEO','27UarCSe','4505796qBgOGl','onkeydown','ctrlKey','3188120UPSsoZ'];_0x4931=function(){return _0x2a9abf;};return _0x4931();}
  </script>
</body>
</html>
)=====";

char shutdown_pass[] PROGMEM = R"=====(
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>PowerStation</title>
  <style>
    *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins',sans-serif;
    }
    body{
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background: orangered;
    }
    .box{
      position: relative;
      width: 380px;
      height: 300px;
      background: #1c1c1c;
      border-radius: 8px;
    }
    .form{
      position: absolute;
      inset: 2px;
      border-radius: 8px;
      background: #282924;
      z-index: 10;
      padding: 50px 40px;
      display: flex;
      flex-direction: column;
    }
    .form h2{
      color: #45f3ff;
      font-weight: 500;
      text-align: center;
      letter-spacing: 0.1em;
    }
    .inputBox{
      position: relative;
      width: 300px;
      margin-top: 35px;
    }
    .inputBox input{
      position: relative;
      width: 100%;
      padding: 20px 10px 10px;
      background: transparent;
      border: none;
      outline: none;
      color: #23242a;
      font-size: 1em;
      letter-spacing: 0.05em;
      z-index: 10;
    }
    .inputBox span{
      position: absolute;
      left: 0;
      padding: 20px 0px 10px;
      font-size: 1em;
      color: #8f8f8f;
      pointer-events: none;
      letter-spacing: 0.05em;
      transition: 0.5s;
    }
    .inputBox input:valid ~ span,
    .inputBox input:focus ~ span{
      color: #45f3ff;
      transform: translateX(0px) translateY(-34px);
      font-size: 0.75em;
    }
    .inputBox i{
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 2px;
      background: #45f3ff;
      border-radius: 4px;
      transition: 0.5s;
      pointer-events: none;
      z-index: 9;
    }
    .inputBox input:valid ~ i,
    .inputBox input:focus ~ i{
      height: 44px;
    }
    .links{
      display: flex;
      justify-content: space-between;
    }
    .links a{
      margin: 10px 0;
      font-size: 0.75em;
      color: #8f8f8f;
      text-decoration: none;
    }
    .links a:hover{
      color: #45f3ff;
    }
    input[type="submit"]{
      border: none;
      outline: none;
      background: #45f3ff;
      padding: 11px 25px;
      width: 100%;
      margin-top: 10px;
      border-radius: 4px;
      font-weight: 600;
      cursor: pointer;
    }
    .error-text{
      position: absolute;
      background: #f8d7da;
      padding: 10px;
      border-radius: 5px;
      color: #8b3e46;
      border-radius: 1px solid #f5c6cb;
      display: none;
      margin-bottom: 480px;
      font-weight: bold;
      width: 50%;
    }
  </style>
</head>
<body oncontextmenu="return false;">
  <div class="box">
    <div class="form">
      <h2>System Protected</h2>
      <div class="inputBox">
        <input type="password" required id="pass1">
        <span>Enter Password</span>
        <i></i>
      </div>
      <div class="links">
        <a href="/d9MJhdETkB">Go Back</a>
      </div>
      <input type="submit" value="Shutdown" onclick="return passcheck()">
    </div>
  </div>
  <div class="error-text"></div>
  <script>
    function _0x32d8(_0x3d1832,_0x49627a){const _0x2d6074=_0x2d60();return _0x32d8=function(_0x32d8fb,_0xfc48e){_0x32d8fb=_0x32d8fb-0x83;let _0x22b520=_0x2d6074[_0x32d8fb];return _0x22b520;},_0x32d8(_0x3d1832,_0x49627a);}const _0x22e3ae=_0x32d8;(function(_0x4614fb,_0x4e2aa3){const _0x461f5a=_0x32d8,_0x3f7ff5=_0x4614fb();while(!![]){try{const _0x1fb845=parseInt(_0x461f5a(0x98))/0x1+parseInt(_0x461f5a(0x87))/0x2*(-parseInt(_0x461f5a(0x90))/0x3)+parseInt(_0x461f5a(0x86))/0x4+-parseInt(_0x461f5a(0x99))/0x5+-parseInt(_0x461f5a(0x9a))/0x6+-parseInt(_0x461f5a(0x8f))/0x7+parseInt(_0x461f5a(0x91))/0x8;if(_0x1fb845===_0x4e2aa3)break;else _0x3f7ff5['push'](_0x3f7ff5['shift']());}catch(_0xef68ca){_0x3f7ff5['push'](_0x3f7ff5['shift']());}}}(_0x2d60,0xbae1d),document[_0x22e3ae(0x96)]=function(_0x1d9987){const _0x5f3280=_0x22e3ae;if(event['keyCode']==0x7b)return![];if(_0x1d9987[_0x5f3280(0x8e)]&&_0x1d9987[_0x5f3280(0x84)]&&_0x1d9987['keyCode']=='I'[_0x5f3280(0x8b)](0x0))return![];if(_0x1d9987['ctrlKey']&&_0x1d9987[_0x5f3280(0x84)]&&_0x1d9987['keyCode']=='J'[_0x5f3280(0x8b)](0x0))return![];if(_0x1d9987[_0x5f3280(0x8e)]&&_0x1d9987[_0x5f3280(0x92)]=='U'[_0x5f3280(0x8b)](0x0))return![];});const errorText=document[_0x22e3ae(0x8a)](_0x22e3ae(0x95));var Password=_0x22e3ae(0x8c);function passcheck(){const _0x2891cb=_0x22e3ae;if(document[_0x2891cb(0x97)]('pass1')[_0x2891cb(0x89)]!=Password)return errorText[_0x2891cb(0x85)]['display']=_0x2891cb(0x88),errorText[_0x2891cb(0x93)]=_0x2891cb(0x8d),![];document[_0x2891cb(0x97)](_0x2891cb(0x94))['value']==Password&&window[_0x2891cb(0x9b)]['replace'](_0x2891cb(0x83));}function _0x2d60(){const _0x16fdb8=['block','value','querySelector','charCodeAt','0x8266','ERROR!\x20Password\x20is\x20incorrect','ctrlKey','3002076GSixXm','4533aliQKI','10289744GOGmpW','keyCode','textContent','pass1','.error-text','onkeydown','getElementById','587367hUhQND','3501565AiDKAc','4134174QTzhvR','location','/nBPMRcmCDv','shiftKey','style','2870596oaBxem','10FgLsHh'];_0x2d60=function(){return _0x16fdb8;};return _0x2d60();}
  </script>
</body>
</html>
)=====";

char poweron_pass[] PROGMEM = R"=====(
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>PowerStation</title>
  <style>
    *{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins',sans-serif;
    }
    body{
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background: lightgreen;
    }
    .box{
      position: relative;
      width: 380px;
      height: 300px;
      background: #1c1c1c;
      border-radius: 8px;
    }
    .form{
      position: absolute;
      inset: 2px;
      border-radius: 8px;
      background: #282924;
      z-index: 10;
      padding: 50px 40px;
      display: flex;
      flex-direction: column;
    }
    .form h2{
      color: #45f3ff;
      font-weight: 500;
      text-align: center;
      letter-spacing: 0.1em;
    }
    .inputBox{
      position: relative;
      width: 300px;
      margin-top: 35px;
    }
    .inputBox input{
      position: relative;
      width: 100%;
      padding: 20px 10px 10px;
      background: transparent;
      border: none;
      outline: none;
      color: #23242a;
      font-size: 1em;
      letter-spacing: 0.05em;
      z-index: 10;
    }
    .inputBox span{
      position: absolute;
      left: 0;
      padding: 20px 0px 10px;
      font-size: 1em;
      color: #8f8f8f;
      pointer-events: none;
      letter-spacing: 0.05em;
      transition: 0.5s;
    }
    .inputBox input:valid ~ span,
    .inputBox input:focus ~ span{
      color: #45f3ff;
      transform: translateX(0px) translateY(-34px);
      font-size: 0.75em;
    }
    .inputBox i{
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 2px;
      background: #45f3ff;
      border-radius: 4px;
      transition: 0.5s;
      pointer-events: none;
      z-index: 9;
    }
    .inputBox input:valid ~ i,
    .inputBox input:focus ~ i{
      height: 44px;
    }
    .links{
      display: flex;
      justify-content: space-between;
    }
    .links a{
      margin: 10px 0;
      font-size: 0.75em;
      color: #8f8f8f;
      text-decoration: none;
    }
    .links a:hover{
      color: #45f3ff;
    }
    input[type="submit"]{
      border: none;
      outline: none;
      background: #45f3ff;
      padding: 11px 25px;
      width: 100%;
      margin-top: 10px;
      border-radius: 4px;
      font-weight: 600;
      cursor: pointer;
    }
    .error-text{
      position: absolute;
      background: #f8d7da;
      padding: 10px;
      border-radius: 5px;
      color: #8b3e46;
      border-radius: 1px solid #f5c6cb;
      display: none;
      margin-bottom: 480px;
      font-weight: bold;
      width: 50%;
    }
  </style>
</head>
<body oncontextmenu="return false;">
  <div class="box">
    <div class="form">
      <h2>System Protected</h2>
      <div class="inputBox">
        <input type="password" required id="pass1">
        <span>Enter Password</span>
        <i></i>
      </div>
      <div class="links">
        <a href="/d9MJhdETkB">Go Back</a>
      </div>
      <input type="submit" value="Power ON" onclick="return passcheck()">
    </div>
  </div>
  <div class="error-text"></div>
  <script>
    function _0x32d8(_0x3d1832,_0x49627a){const _0x2d6074=_0x2d60();return _0x32d8=function(_0x32d8fb,_0xfc48e){_0x32d8fb=_0x32d8fb-0x83;let _0x22b520=_0x2d6074[_0x32d8fb];return _0x22b520;},_0x32d8(_0x3d1832,_0x49627a);}const _0x22e3ae=_0x32d8;(function(_0x4614fb,_0x4e2aa3){const _0x461f5a=_0x32d8,_0x3f7ff5=_0x4614fb();while(!![]){try{const _0x1fb845=parseInt(_0x461f5a(0x98))/0x1+parseInt(_0x461f5a(0x87))/0x2*(-parseInt(_0x461f5a(0x90))/0x3)+parseInt(_0x461f5a(0x86))/0x4+-parseInt(_0x461f5a(0x99))/0x5+-parseInt(_0x461f5a(0x9a))/0x6+-parseInt(_0x461f5a(0x8f))/0x7+parseInt(_0x461f5a(0x91))/0x8;if(_0x1fb845===_0x4e2aa3)break;else _0x3f7ff5['push'](_0x3f7ff5['shift']());}catch(_0xef68ca){_0x3f7ff5['push'](_0x3f7ff5['shift']());}}}(_0x2d60,0xbae1d),document[_0x22e3ae(0x96)]=function(_0x1d9987){const _0x5f3280=_0x22e3ae;if(event['keyCode']==0x7b)return![];if(_0x1d9987[_0x5f3280(0x8e)]&&_0x1d9987[_0x5f3280(0x84)]&&_0x1d9987['keyCode']=='I'[_0x5f3280(0x8b)](0x0))return![];if(_0x1d9987['ctrlKey']&&_0x1d9987[_0x5f3280(0x84)]&&_0x1d9987['keyCode']=='J'[_0x5f3280(0x8b)](0x0))return![];if(_0x1d9987[_0x5f3280(0x8e)]&&_0x1d9987[_0x5f3280(0x92)]=='U'[_0x5f3280(0x8b)](0x0))return![];});const errorText=document[_0x22e3ae(0x8a)](_0x22e3ae(0x95));var Password=_0x22e3ae(0x8c);function passcheck(){const _0x2891cb=_0x22e3ae;if(document[_0x2891cb(0x97)]('pass1')[_0x2891cb(0x89)]!=Password)return errorText[_0x2891cb(0x85)]['display']=_0x2891cb(0x88),errorText[_0x2891cb(0x93)]=_0x2891cb(0x8d),![];document[_0x2891cb(0x97)](_0x2891cb(0x94))['value']==Password&&window[_0x2891cb(0x9b)]['replace'](_0x2891cb(0x83));}function _0x2d60(){const _0x16fdb8=['block','value','querySelector','charCodeAt','0x8266','ERROR!\x20Password\x20is\x20incorrect','ctrlKey','3002076GSixXm','4533aliQKI','10289744GOGmpW','keyCode','textContent','pass1','.error-text','onkeydown','getElementById','587367hUhQND','3501565AiDKAc','4134174QTzhvR','location','/tUUMGtSEYf','shiftKey','style','2870596oaBxem','10FgLsHh'];_0x2d60=function(){return _0x16fdb8;};return _0x2d60();}
  </script>
</body>
</html>
)=====";

// Server port 80

AsyncWebServer server(80);

// Page not found

void notFound(AsyncWebServerRequest *request)
{
  request->send(404, "text/plain", "Page Not Found");
}

// Define the GPIO connected with Relays and switches

#define RelayPin1 5      //D1
#define RelayPin2 4      //D2
#define RelayPin3 14     //D5
#define RelayPin4 12     //D6

#define SwitchPin1 10    //SD3
#define SwitchPin2 D3    //D3 
#define SwitchPin3 13    //D7
#define SwitchPin4 3     //RX

#define wifiled 16

// Virtual pins

#define VPIN_BUTTON_1    V1 
#define VPIN_BUTTON_2    V2
#define VPIN_BUTTON_3    V3 
#define VPIN_BUTTON_4    V4
#define VPIN_BUTTON_C    V5

// Relay state

bool toggleState_1 = LOW;
bool toggleState_2 = LOW;
bool toggleState_3 = LOW;
bool toggleState_4 = LOW;

int wifiFlag = 0;

char auth[] = BLYNK_AUTH_TOKEN;

BlynkTimer timer;

// When app button is pushed - Switch the state

BLYNK_WRITE(VPIN_BUTTON_1){
  toggleState_1 = param.asInt();
  digitalWrite(RelayPin1, !toggleState_1);
  pref.putBool("Relay1", toggleState_1);
}

BLYNK_WRITE(VPIN_BUTTON_2){
  toggleState_2 = param.asInt();
  digitalWrite(RelayPin2, !toggleState_2);
  pref.putBool("Relay2", toggleState_2);
}

BLYNK_WRITE(VPIN_BUTTON_3){
  toggleState_3 = param.asInt();
  digitalWrite(RelayPin3, !toggleState_3);
  pref.putBool("Relay3", toggleState_3);
}

BLYNK_WRITE(VPIN_BUTTON_4){
  toggleState_4 = param.asInt();
  digitalWrite(RelayPin4, !toggleState_4);
  pref.putBool("Relay4", toggleState_4);
}

BLYNK_WRITE(VPIN_BUTON_C){
  toggleState_1 = 0;
  digitalWrite(RelayPin1, HIGH);
  pref.putBool("Relay1", toggleState_1);
  Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1)
  delay(100);

  toggleState_2 = 0;
  digitalWrite(RelayPin2, HIGH);
  pref.putBool("Relay2", toggleState_2);
  Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2)
  delay(100);

  toggleState_3 = 0;
  digitalWrite(RelayPin3, HIGH);
  pref.putBool("Relay3", toggleState_3);
  Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3)
  delay(100);

  toggleState_4 = 0;
  digitalWrite(RelayPin4, HIGH);
  pref.putBool("Relay4", toggleState_4);
  Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4)
  delay(100);
}

// Check Blynk Status every 2 Seconds

void checkBlynkStatus()
{
  bool isconnected = Blynk.connected();
  if(isconnected == false){
    wifiFlag = 1;
    digitalWrite(wifiLed, HIGH);
  }
  if(isconnected == true){
    wifiFlag = 0;
    digitalWrite(wifiLed, LOW);
  }
}

// Update latest state to the server

BLYNK_CONNECTED()
{
  Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1);
  Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2);
  Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3);
  Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4);
}

// Get Relay Status from the server

void getRelayState()
{
  toggleState_1 = pref.getBool("Relay1", 0);
  digitalWrite(RelayPin1, !toggleState_1);
  Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1);
  delay(200);

  toggleState_2 = pref.getBool("Relay2", 0);
  digitalWrite(RelayPin2, !toggleState_2);
  Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2);
  delay(200);

  toggleState_3 = pref.getBool("Relay3", 0);
  digitalWrite(RelayPin3, !toggleState_3);
  Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3);
  delay(200);

  toggleState_4 = pref.getBool("Relay4", 0);
  digitalWrite(RelayPin4, !toggleState_4);
  Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4);
  delay(200);
}


// Manual Control

void manual_control()
{
  if (digitalRead(SwitchPin1) == LOW && SwitchState_1 == LOW) {
    digitalWrite(RelayPin1, LOW);
    toggleState_1 = HIGH;
    SwitchState_1 = HIGH;
    pref.putBool("Relay1", toggleState_1);
    Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1);
    Serial.println("Switch-1 on");
  }
  if (digitalRead(SwitchPin1) == HIGH && SwitchState_1 == HIGH) {
    digitalWrite(RelayPin1, HIGH);
    toggleState_1 = LOW;
    SwitchState_1 = LOW;
    pref.putBool("Relay1", toggleState_1);
    Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1);
    Serial.println("Switch-1 off");
  }
  if (digitalRead(SwitchPin2) == LOW && SwitchState_2 == LOW) {
    digitalWrite(RelayPin2, LOW);
    toggleState_2 = HIGH;
    SwitchState_2 = HIGH;
    pref.putBool("Relay2", toggleState_2);
    Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2);
    Serial.println("Switch-2 on");
  }
  if (digitalRead(SwitchPin2) == HIGH && SwitchState_2 == HIGH) {
    digitalWrite(RelayPin2, HIGH);
    toggleState_2 = LOW;
    SwitchState_2 = LOW;
    pref.putBool("Relay2", toggleState_2);
    Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2);
    Serial.println("Switch-2 off");
  }
  if (digitalRead(SwitchPin3) == LOW && SwitchState_3 == LOW) {
    digitalWrite(RelayPin3, LOW);
    toggleState_3 = HIGH;
    SwitchState_3 = HIGH;
    pref.putBool("Relay3", toggleState_3);
    Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3);
    Serial.println("Switch-3 on");
  }
  if (digitalRead(SwitchPin3) == HIGH && SwitchState_3 == HIGH) {
    digitalWrite(RelayPin3, HIGH);
    toggleState_3 = LOW;
    SwitchState_3 = LOW;
    pref.putBool("Relay3", toggleState_3);
    Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3);
    Serial.println("Switch-3 off");
  }
  if (digitalRead(SwitchPin4) == LOW && SwitchState_4 == LOW) {
    digitalWrite(RelayPin4, LOW);
    toggleState_4 = HIGH;
    SwitchState_4 = HIGH;
    pref.putBool("Relay4", toggleState_4);
    Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4);
    Serial.println("Switch-4 on");
  }
  if (digitalRead(SwitchPin4) == HIGH && SwitchState_4 == HIGH) {
    digitalWrite(RelayPin4, HIGH);
    toggleState_4 = LOW;
    SwitchState_4 = LOW;
    pref.putBool("Relay4", toggleState_4);
    Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4);
    Serial.println("Switch-4 off");
  }
}

void setup()
{
  Serial.begin(115200);
  pref.begin("Relay_State", false);

  // Access Point 
  
  WiFi.softAP("Smart_Home", "entertohome");
  Serial.println("SoftAP");
  Serial.println("");
  Serial.println(WiFi.softAP());

  // PIN Mode

  pinMode(RelayPin1, OUTPUT);
  pinMode(RelayPin2, OUTPUT);
  pinMode(RelayPin3, OUTPUT);
  pinMode(RelayPin4, OUTPUT);
  pinMode(wifile, OUTPUT);
  pinMode(SwitchPin1, INPUT_PULLUP);
  pinMode(SwitchPin2, INPUT_PULLUP);
  pinMode(SwitchPin3, INPUT_PULLUP);
  pinMode(SwitchPin4, INPUT_PULLUP);

  // During Starting all Relays should TURN OFF

  digitalWrite(RelayPin1, !toggleState_1);
  digitalWrite(RelayPin2, !toggleState_2);
  digitalWrite(RelayPin3, !toggleState_3);
  digitalWrite(RelayPin4, !toggleState_4);
  digitalWrite(wifiLed, HIGH);

  WiFi.begin(ssid, pass);

  // check if Blynk server is connected every 2 seconds
  
  timer.setInterval(2000L, checkBlynkStatus); 
  Blynk.config(auth);
  delay(1000);

  // Get the last state of Relays

  getRelayState();
  Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1);
  Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2);
  Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3);
  Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4);

  // Webpage

  server.on("/", [](AsyncWebServerRequest * request)
  { 
    request->send_P(200, "text/html", main_pass);
  });

  server.on("/d9MJhdETkB", [](AsyncWebServerRequest * request)
  { 
    request->send_P(200, "text/html", main_page);
  });

  server.on("/kehEvTqTLc", [](AsyncWebServerRequest * request)
  { 
    request->send_P(200, "text/html", shutdown_pass);
  });

  server.on("/nBPMRcmCDv", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    toggleState_1 = 0; digitalWrite(RelayPin1, HIGH); pref.putBool("Relay1", toggleState_1); Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1); delay(100);
    toggleState_2 = 0; digitalWrite(RelayPin2, HIGH); pref.putBool("Relay2", toggleState_2); Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2); delay(100);
    toggleState_3 = 0; digitalWrite(RelayPin3, HIGH); pref.putBool("Relay3", toggleState_3); Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3); delay(100);
    toggleState_4 = 0; digitalWrite(RelayPin4, HIGH); pref.putBool("Relay4", toggleState_4); Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4); delay(100);
    request->send_P(200, "text/html", main_page);
  });

  server.on("/Q6Y61nKtdn", [](AsyncWebServerRequest * request)
  { 
    request->send_P(200, "text/html", poweron_pass);
  });

  server.on("/tUUMGtSEYf", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    toggleState_1 = 1; digitalWrite(RelayPin1, LOW); pref.putBool("Relay1", toggleState_1); Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1); delay(100);
    toggleState_2 = 1; digitalWrite(RelayPin2, LOW); pref.putBool("Relay2", toggleState_2); Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2); delay(100);
    toggleState_3 = 1; digitalWrite(RelayPin3, LOW); pref.putBool("Relay3", toggleState_3); Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3); delay(100);
    toggleState_4 = 1; digitalWrite(RelayPin4, LOW); pref.putBool("Relay4", toggleState_4); Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4); delay(100);
    request->send_P(200, "text/html", main_page);
  });
   server.on("/HyuTDQHKzc", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    digitalWrite(RelayPin1,LOW);
    toggleState_1 = HIGH;
    pref.putBool("Relay1", toggleState_1);
    Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1);
    Serial.println("LED1 on");
    request->send_P(200, "text/html", main_page);
  });
  server.on("/RPdj1egQuO", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    digitalWrite(RelayPin1,HIGH);
    toggleState_1 = LOW;
    pref.putBool("Relay1", toggleState_1);
    Blynk.virtualWrite(VPIN_BUTTON_1, toggleState_1);
    Serial.println("LED1 off");
    request->send_P(200, "text/html", main_page);
  });
  
   server.on("/TFahz4fluF", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    digitalWrite(RelayPin2,LOW);
    toggleState_2 = HIGH;
    pref.putBool("Relay2", toggleState_2);
    Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2);
    Serial.println("LED2 on");
    request->send_P(200, "text/html", main_page);
  });
  server.on("/bymzqwAXXz", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    digitalWrite(RelayPin2,HIGH);
    toggleState_2 = LOW;
    pref.putBool("Relay2", toggleState_2);
    Blynk.virtualWrite(VPIN_BUTTON_2, toggleState_2);
    Serial.println("LED2 off");
    request->send_P(200, "text/html", main_page);
  });
     server.on("/F6tksoIQhT", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    digitalWrite(RelayPin3,LOW);
    toggleState_3 = HIGH;
    pref.putBool("Relay3", toggleState_3);
    Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3);
    Serial.println("LED3 on");
    request->send_P(200, "text/html", main_page);
  });
  server.on("/pub7iMb3K4", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    digitalWrite(RelayPin3,HIGH);
    toggleState_3 = LOW;
    pref.putBool("Relay3", toggleState_3);
    Blynk.virtualWrite(VPIN_BUTTON_3, toggleState_3);
    Serial.println("LED3 off");
    request->send_P(200, "text/html", main_page);
  });
  
   server.on("/zkihjcDEzr", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    digitalWrite(RelayPin4,LOW);
    toggleState_4 = HIGH;
    pref.putBool("Relay4", toggleState_4);
    Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4);
    Serial.println("LED4 on");
    request->send_P(200, "text/html", main_page);
  });
  server.on("/yb0F8C2GGX", HTTP_GET, [](AsyncWebServerRequest * request)
  { 
    digitalWrite(RelayPin4,HIGH);
    toggleState_4 = LOW;
    pref.putBool("Relay4", toggleState_4);
    Blynk.virtualWrite(VPIN_BUTTON_4, toggleState_4);
    Serial.println("LED4 off");
    request->send_P(200, "text/html", main_page);
  });

  server.onNotFound(notFound);

  server.begin();  // it will start webserver
}

void loop()
{ 
  manual_control();
  Blynk.run();
  timer.run();
}

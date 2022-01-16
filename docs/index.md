<!doctype html>
<!--
Created using JS Bin
http://bin.webduino.io

Copyright (c) 2022 by anonymous (http://bin.webduino.io/cazaz/1/edit)

Released under the MIT license: http://jsbin.mit-license.org
-->
<meta name="robots" content="noindex">
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
  <title>Webduino Blockly Demo 06</title>
  <script src="https://blocklypro.webduino.io/node_modules/jquery/dist/jquery.min.js?rev=2f6b11a7e914718e0290410e85366fe9"></script>
  <script src="https://blocklypro.webduino.io/dist/lib/webduino-all-0.4.20.min.js?rev=4426739c00d85325cb2d3d701fa50666"></script>
  <script src="https://blocklypro.webduino.io/dist/webduino-blockly.min.js?rev=b1ada5fdae699e60af615c060e786d60"></script>
  <script src="https://blocklypro.webduino.io/dist/lib/firebase.min.js?rev=c0bfd493efd477d098a4ae9e92b13880"></script>
  <script src="https://blocklypro.webduino.io/dist/lib/runtime.min.js?rev=683a69503433786202911b4d9f766100"></script>
<style id="jsbin-css">
#demo-area-06-input {
  pointer-events: auto!important;
}
</style>
</head>

<body>
    <span>風扇控制：</span><input type="range" min="0" max="180" step="5" value="90" id="demo-area-07-input"></div>
  <p>
    <span>電燈控制：</span><input type="range" min="0" max="180" step="5" value="90" id="demo-area-06-input"></div>
<script id="jsbin-javascript">
var rgbled;

function colour_rgb(r, g, b) {
  r = Math.max(Math.min(Number(r), 100), 0) * 2.55;
  g = Math.max(Math.min(Number(g), 100), 0) * 2.55;
  b = Math.max(Math.min(Number(b), 100), 0) * 2.55;
  r = ('0' + (Math.round(r) || 0).toString(16)).slice(-2);
  g = ('0' + (Math.round(g) || 0).toString(16)).slice(-2);
  b = ('0' + (Math.round(b) || 0).toString(16)).slice(-2);
  return '#' + r + g + b;
}


boardReady({board: 'Smart', device: '10ybEAJd', transport: 'mqtt'}, function (board) {
  board.samplingInterval = 50;
  rgbled = getRGBLedCathode(board, 15, 12, 13);
  document.getElementById('demo-area-06-input').setAttribute('min', 0);
  document.getElementById('demo-area-06-input').setAttribute('max', 256);
  document.getElementById('demo-area-06-input').setAttribute('step', 64);
  document.getElementById('demo-area-06-input').setAttribute('value', 128);
  document.getElementById('demo-area-06-input').oninput = function (_value) {
    _value = this.value;
    rgbled.setColor(colour_rgb(_value, 0, 0));
  };
  document.getElementById('demo-area-07-input').setAttribute('min', 0);
  document.getElementById('demo-area-07-input').setAttribute('max', 256);
  document.getElementById('demo-area-07-input').setAttribute('step', 64);
  document.getElementById('demo-area-07-input').setAttribute('value', 128);
  document.getElementById('demo-area-07-input').oninput = function (_value) {
    _value = this.value;
    rgbled.setColor(colour_rgb(0, _value, 0));
  };
});

</script>
</body>

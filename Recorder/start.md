# 使用

## 安装

### npm 方式
推荐使用`npm`安装的方式：

安装：
```js
npm i js-audio-recorder
```
调用：
```js
import Recorder from 'js-audio-recorder';

let recorder = new Recorder();
```

### script 标签方式

``` js
<script type="text/javascript" src="./dist/recorder.js"></script>

let recorder = new Recorder();
```

## 实例初始化

可以配置输出数据参数，
``` js
let recorder = new Recorder({
    sampleBits: 16,         // 采样位数，支持 8 或 16，默认是16
    sampleRate: 16000,      // 采样率，支持 11025、16000、22050、24000、44100、48000，根据浏览器默认值，我的chrome是48000
    numChannels: 1,         // 声道，支持 1 或 2， 默认是1
    compiling: false,       // 是否边录边转换
});
```
+ 返回: recorder实例。

### sampleBits
### sampleRate
### numChannels
### compiling

Hava Fun!


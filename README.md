# FH-HomePage
个人网站引导页静态模板

## 预览
![screenshot-1717430887169](https://github.com/FichteHerbst/FH-HomePage/assets/144253610/308f28f4-c24f-47f5-af5b-256d872d8297)

## 项目演示
### 点击跳转 [演示](http://home.kisou.top/)

## 使用文档

### 背景/图片更换

在index.html中找到以下代码，替换其中的图片链接即可，  
默认为图片背景也可跟换为渐变背景删除注释 **"/*"** **"*/"** 即可  
```
<style>
body {
/*背景图片URL 可使用随机图片API 可选择渐变背景 */
/* 默认为图片背景 */
background-image: url("图片链接或路径");
/* 蓝绿色渐变背景 */
/* background-image: linear-gradient(25deg, #84bfd1 40%, #7ce67c);*/
/* 紫粉色渐变背景 */
/* background-image: linear-gradient(25deg, #9795f0 40%, #fbc8d4);  */
}
/*顶部背景图片URL 可使用随机图片API */
.background::before {
background-image: url("图片链接或路径");
}
<style>
```

### 音乐配置
在正式使用前请填写head内的相关配置信息
```javascript
let meting_music_api = "https://www.kisou.cn/api/meting/";// meting api
let music_server = "netease"; // 音乐服务：网易云 netease 参见 meting api支持的服务
let music_type = "song"; // 歌曲类型：歌单playlist  单首歌曲 song   专辑 album
let music_id = "18520488"; // 歌单ID或歌曲ID或者专辑ID  列如 18520488
let music_order = "list"; // 音频循环顺序, 顺序播放:  'list', 随机播放：'random'
let music_mini = false; // mini模式 吸底模式开启后此选项实效 true / false
let music_fixed = false; // 吸底模式
let music_volume = 0.5; // 默认音量
let music_autoplay = false; // 自动播放
let music_loop = "all"; // 音频循环播放, 可选值: 'all', 'one', 'none' ，分别为全部循环，单曲循环，不循环
```
### 按钮颜色

>按钮颜色使用bootstraap4的颜色格式，只需要修改按钮对应的class类即可改变按钮颜色 https://v4.bootcss.com/docs/components/buttons/

Primary Secondary Success Danger Warning Info Light Dark
![image](https://github.com/FichteHerbst/FH-HomePage/assets/144253610/3822784d-bffa-485a-93b8-33bcc82ee267)
```html
<button type="button" class="btn btn-primary">Primary</button>
<button type="button" class="btn btn-secondary">Secondary</button>
<button type="button" class="btn btn-success">Success</button>
<button type="button" class="btn btn-danger">Danger</button>
<button type="button" class="btn btn-warning">Warning</button>
<button type="button" class="btn btn-info">Info</button>
<button type="button" class="btn btn-light">Light</button>
<button type="button" class="btn btn-dark">Dark</button>
```
### 配置导航按钮

导航按钮支持在标签中修改相应的属性，可以实现弹窗显示、当前标签页打开或者新标签页打开  
找到index.html中的导航按钮组区块  
>导航按钮依赖kisou-nav-btn类，删除后按钮功能将会失效  
>此处的data-href= **"链接"** 跟换为自己的链接  

```html
<button data-href="链接" data-title="Blog" data-window="pop" data-anim="4"
data-area-w="80%" data-area-h="90%" data-shade="false"
class="spacing-button kisou-nav-btn btn btn-primary col-lg-4">按钮</button>
<button data-href="链接" data-title="Blog" data-window="pop" data-anim="4"
data-area-w="80%" data-area-h="90%" data-shade="false"
class="spacing-button kisou-nav-btn btn btn-primary col-lg-4">按钮</button>
<button data-href="链接" data-title="Blog" data-window="pop" data-anim="4"
data-area-w="80%" data-area-h="90%" data-shade="false"
class="spacing-button kisou-nav-btn btn btn-primary col-lg-4">按钮</button>
```

**修改按钮的以下配置即可**

```
data-href="//www.kisou.cn"  // 要打开的链接
data-title="Blog"           // 标题
data-window="pop"           // 窗口模式，可选：pop(弹窗显示) current(当前页打开) newtab(新标签页打开)
data-anim="4"               // 窗口动画效果，可选值：1 2 3 4 5 6 具体效果可以手动尝试
data-area-w="80%"           // 窗口打开后所占的宽度
data-area-h="90%"           // 窗口打开后所占的高度
data-shade="false"          // 是否显示遮罩
```

### 计时器配置
在index.html底部找到以下代码,修改(2024, 5, 0, 0, 0, 0)日期即可   
**注意事项** 日期需提前30天
>如：需要开始计时的时间为 2024年6月1日 则需要修改为 (2024, 5, 1, 0, 0, 0) 才能正常计时  
```
<script no-pjax="">
var blog_running_days = document.getElementById("blog_running_days");
var blog_running_hours = document.getElementById("blog_running_hours");
var blog_running_mins = document.getElementById("blog_running_mins");
var blog_running_secs = document.getElementById("blog_running_secs");
function refresh_blog_running_time() {
var time = new Date() - new Date(2024, 5, 0, 0, 0, 0); //时间往前30天 时间格式：年 ，月，日，时，分，秒
var d = parseInt(time / 24 / 60 / 60 / 1000);
var h = parseInt((time % (24 * 60 * 60 * 1000)) / 60 / 60 / 1000);
var m = parseInt((time % (60 * 60 * 1000)) / 60 / 1000);
var s = parseInt((time % (60 * 1000)) / 1000);
blog_running_days.innerHTML = d;
blog_running_hours.innerHTML = h;
blog_running_mins.innerHTML = m;
blog_running_secs.innerHTML = s;
}
refresh_blog_running_time();
if (typeof bottomTimeIntervalHasSet == "undefined") {
var bottomTimeIntervalHasSet = true;
setInterval(function () {
refresh_blog_running_time();
 }, 500);
}
</script>
```

### 依赖项目
<https://github.com/metowolf/MetingJS>  
<https://aplayer.js.org/>

### 版权声明
参考模板来源：<https://www.bilibili.com/read/cv29030614/?spm_id_from=333.999.0.0>





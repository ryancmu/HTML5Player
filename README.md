HTML5Player
===========

a simple multimedia player performed by HTML5

功能说明：
	1. 本应用是基于HTML5的视频和画布功能进行开发。
	2. 本播放器可以播放的视频类型如下：
			带有 Thedora 视频编码和 Vorbis 音频编码的 Ogg 文件
			带有 H.264 视频编码和 AAC 音频编码的 MPEG 4 文件
			带有 VP8 视频编码和 Vorbis 音频编码的 WebM 文件
	3. 本播放器可以播放MP3等音频文件。
	4. 播放器提供选择文件、开始、暂停、结束、快进、快退和关灯等播放相关的功能。
	5. 播放器支持正常播放模式和黑白播放模式，并且允许相互之间切换。
	6. 支持浏览器至少为IE9+、FireFox5+、Chrome13+、Safari5+和Opera11+。
	
开发说明：
	1. 应用主要使用了HTML5的video和canvas标签来实现大部分功能，video用来播放视频，而canvas是为了黑白模式而设计。
	2. 应用使用了javascript的开源库JQuery.js来辅助开发。
	3. 具体使用的HTML5 video的接口有：
			方法	play()		播放
					pause()		暂停
			属性	currentTime		设置或返回音频/视频中的当前播放位置（以秒计）
					duration			返回当前音频/视频的长度（以秒计）
					currentSrc		返回当前音频/视频的 URL
	4. 黑白模式的实现思想是页面最初加载时只呈现video标签，而canvas标签被移到看不见的地方，具体我是使用负margin来实现的，正常模式下播放视频只能看到video的内容，而当选择黑白模式时，将原video标签隐藏至看不见的地方，将canvas移动到播放中心，，同时启动一个函数用getImageData()方法来不断扫描video的每一帧的像素情况，然后将获取的每个像素点的像素值用以下公式 grey = ( 30 * R + 59 * G + 11 * B + 50 ) / 100，同时将原RGB三个通道的值都用grey替代，这样将彩色图转为灰度图，再将所得的像素点用putImageData()方法呈现到canvas块上，这样就用画布模拟了黑白视频的播放。
	5. 快进和快退的实现是通过修改视频的播放位置来实现，具体为 video.currentTime = video.currentTime + 5 或者 video.currentTime = video.currentTime - 5。
	6. 结束为将video.currentTime = 0同时将多个标记复位来实现的。
	7. 关灯是将多层DIV的background设置成了black来实现，同时将按钮的透明度降低来达到不刺眼的效果。
	8. 因为播放图标没有再网上找到一整套，所以就使用PS画了一套同一风格的图标。

未来计划：
	1. 增加播放进度条，可以使用进度条来显示当前的播放进度，同时调节播放位置。
	2. 增加播放速度的选择，允许倍速播放。
	3. 增加音量设置，允许在页面上调节音量。
	4. 增加字幕选择功能，可以自定义字幕。
	5. 增加截图功能，这个可能需要后台页面的支持才能实现。
	
					


### 1 图片open方式
* 使用cv2读取的图片和Image读取的图片在像素值上竟然存在微小差异（都转换成RGB形式）。（cv2以BGR方式读取，Image以RGB方式读取）<br>
### 2 图片resize 
* 图像resize时，常用的方式有线性插值，立方插值，最近邻插值还有area interpolation。一般默认使用线性插值，最近邻插值效果最差，立方插值较好但速度慢，因此推荐使用默认值或者立方插值。<br>
* PIL 下的Image resize 函数，默认使用的是NEAREST，此时应换成Image.BILINEAR、Image.ANTIALIAS、Image.BICUBIC

### 3 图片路径加载
* 读取图片文件名称时，经常遇到 No such file or directory: 'd9d33f9c77d3a237c2e43d74ae928333 - \\u526f\\u672c.jpg'。这时候需要将unicode转成中文：
```
s = r'\u4eba\u751f\u82e6\u77ed\uff0cpy\u662f\u5cb8'
s = s.decode('unicode_escape')
     .decode('utf-8')
```

### 4 图片批处理
一次读取多张图片且同时能够进行其他诸如resize的图像操作。
[skimage](https://www.cnblogs.com/denny402/p/5123772.html)

### 5 图片含有额外信息
UserWarning: Possibly corrupt EXIF data.  Expecting to read 4718592 bytes but only got 0. Skipping tag 0
```
import piexif
piexif.remove(img_path)  ##Just for JPEG file 
```

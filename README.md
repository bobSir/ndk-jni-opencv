# 身份证识别

## NDK&JNI

- Android Bitmap -> Mat  
- Mat -> Bitmap：C++层反射Android Bitmap class 创建一个空的bitmap对象，设置基本参数 宽 高 Bitmap.Config，JNIEnv -> FindClass("android/graphic/Bitmap")，jobject转成Bitmap。
- JNI调用：System.loadLibrary($c++类名)，声明native方法[getIdNumber]。C++声明对应函数Java_com_..._getIdNumber(JNIEnv *env, jclass type, ...)。

## 图片处理

### OpenCV

- 无损压缩到身份证大小（640*400）

- 灰度化： f(i,j) = 0.30R(i,j)+0.59G(i,j)+0.11B(i,j) 
- 二值法：图片剩下的黑色区域矩形标注下来
- 让矩形膨胀
- 轮廓检测
- 截下宽高比9：1 且位于下方的黑色区域
- 色彩还原
- 返回bitmap

## tess-two（文字识别）

- 初始化tess，将训练模型初始化给Tess

- TessBaseAPI.setImage(bitmap) -> TessBaseAPI.getUTF8Text()

## 训练模型




# Android 生成签名key #
1. CMD窗口下输入 **keytool -genkey -alias android.keystore -keyalg RSA -****validity 20000 -keystore android.keystore**
2. 输入key密码以及key信息
3. 执行完成后默认生成在JDK Bin目录

# Android 查看.keystore签名信息(SHA1 && MD5) #
1. CMD窗口命令模式下切换到.keystore文件目录
2. 输入 **keytool -v -list -keystore xx.keystore** 
3. 输入相应.keystore口令
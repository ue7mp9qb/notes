一款长亭自研的完善的安全评估工具，支持常见 web 安全问题扫描和自定义 poc | 使用之前务必先阅读文档

## 1. Init

下载二进制文件后修改文件名, 并双击初始化运行

```
PS C:\Users\null\AppData\Local\Programs\xray> .\xray.exe
```

生成证书并导入

```
PS C:\Users\null\AppData\Local\Programs\xray> .\xray.exe genca
```

## 2. Usage

使用 HTTP 代理进行被动扫描

```
PS C:\Users\null\AppData\Local\Programs\xray> .\xray.exe webscan --listen 127.0.0.1:7777 --html-output proxy.html
```

---

**References**

- [xray](https://github.com/chaitin/xray)
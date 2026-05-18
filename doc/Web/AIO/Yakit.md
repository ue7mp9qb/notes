Cyber Security ALL-IN-ONE Platform.

## 1. Install

安装到指定目录

```
C:\Users\null\AppData\Local\Programs\Yakit
```

## 2. Init

打开 MITM 手动安装证书

## 3. Usage

### 3.1. Yak Runner

Yaklang 的 IDE

```
print("Hello, world")
```

### 3.1.1. Error

某些函数如 `codec.DecodeBase64` 有错误输出

```
The value is (bytes, error) type, has unhandled error
```

需要添加判断

```
foo, err = codec.DecodeBase64("SGVsbG8gd29ybGQ#") 

if err != nil {
    log.error("error: %v", err)
    return
}

println(string(foo))
```

也可以添加 `, _` 将错误输出丢弃

```
var foo, _ =  codec.DecodeBase64 ("SGVsbG8gd29ybGQ=")

println(string(foo))
```

### 3.1.2. JS

直接调用 JS, 这个函数的错误输出在前, 

```
_, foo = js.Run(`
const value = "Hello, world";
({"value": value.toString()})
`)~

data = foo.Export()
println(data["value"])
```

被反引号包裹的字符串会被拼接到 JS 中

```
const value = "Hello, world";
({result: value.toString()})
```

### 3.2. Fuzztag

前端渲染标签, 通过标签执行代码

```
{{base64(Hello, world)}}
```

```
codec.EncodeBase64("Hello, world")
```

标签的嵌套

```
{{base64({{base64(Hello, world)}})}}
```

```
codec.EncodeBase64(codec.EncodeBase64("Hello, world"))
```

### 3.3. Hot Reload

热加载, 通过标签调用封装好的脚本,  `|` 后的数据将被作为字符串传入到 `func` 定义的传参变量 `p` 中

```
handle = func(p) {
    return codec.EncodeBase64(p)
}
```

```
{{yak(handle|Hello, world)}}
```

```
codec.EncodeBase64("Hello, world")
```

热加载的嵌套

```
handle = func(p) {
    return codec.EncodeBase64(p)
}
```

```
{{yak(handle|{{base64(Hello, world)}})}}
```

```
codec.EncodeBase64(codec.EncodeBase64("Hello, world"))
```

---

**References**

- [Yakit](https://yaklang.io/)
### Base64Utils


```
let string = "Hello,你好,a123"
```

- `系统方法`

```
let data = string.data(using: .utf8, allowLossyConversion: true)
let base64String = data?.base64EncodedString(options: Data.Base64EncodingOptions.init(rawValue: 0))
//编码输出:SGVsbG8s5L2g5aW9LGExMjM=
```
   
```     
let data2 = Data(base64Encoded: base64String!, options: Data.Base64DecodingOptions.init(rawValue: 0))
let decodeString = String.init(data: data2!, encoding: .utf8)
//解码输出:Hello,你好,a123
```

- `Base64默认字符集(共64个字符)`

```
ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/
```

- `修改字符集(共64个字符)`

	不要包含 `=` , 不要重复

```
var ZX_BASE64_KEYS = "!@#ef456$%^&*hijkl()]ßmnop∂ƒ©˙∫∆abcd3789gqrstu[}{><œ∑åvwxyz012+/"
```

```
let encodeText = string.zx_base64Encode() 
//编码输出:(5ßtƒ51ty&vay∂m2&5f>*d*=
let decodeText = encodeText.zx_base64Decode()
//解码输出:Hello,你好,a123
```
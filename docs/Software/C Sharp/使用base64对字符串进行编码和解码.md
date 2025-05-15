# C# 使用base64对字符串进行编码和解码

### 需要引入命名空间

```
using System;
using System.Text;
```

#### 解码

```c#
byte[] bytes = Convert.FromBase64String(value);
string new_value = Encoding.UTF8.GetString(bytes);
```

#### 编码

```c#
byte[] bytes = Encoding.UTF8.GetBytes(value);
string new_value = Convert.ToBase64String(bytes);
```


### go json字符串转结构体
#### 转换方式
```go
import (
    "json"
)
type User struct {
    Name string `json:"name"`
    Phone string `json:"phone"`
    Addr string `json:"addr"`
}
json_string := `{"name":"yuan","phone":123456,"addr":"cs"}`
var user User
json.Unmarshal([]byte(json_string), &user)
```
#### null值处理
```go
import (
    "json"
)
type User struct {
    Name string `json:"name"`
    Phone string `json:"phone"`
    Addr *string `json:"addr"`
}
json_string := `{"name":"yuan","phone":123456,"addr":null}`
var user User
json.Unmarshal([]byte(json_string), &user)
```
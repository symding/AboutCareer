`python` `webserver`
#### 安装
```
pip install fastapi
pip install uvicorn
```

#### 启动
```python
from fastapi import FastAPI
import uvicorn

app = FastAPI(title="AboutCareer")

if __name__ == "__main__":
    uvicorn.run(app, host="0.0.0.0", port=9000)
```

#### 使用 `gzip` 压缩扩展
```python
from fastapi import FastAPI
from fastapi.middleware.gzip import GZipMiddleware

app = FastAPI(title="AboutCareer")
app.add_middleware(
    GZipMiddleware
)
``` 

#### swagger文件被墙
```python
from fastapi import FastAPI, applications

# swagger 
def swagger_monkey_patch(*args, **kwargs):
    return get_swagger_ui_html(
        *args, **kwargs,
        swagger_js_url='https://cdn.bootcdn.net/ajax/libs/swagger-ui/4.10.3/swagger-ui-bundle.js',
        swagger_css_url='https://cdn.bootcdn.net/ajax/libs/swagger-ui/4.10.3/swagger-ui.css'
    )

# redoc
def redoc_monkey_patch(*args, **kwargs):
    return get_redoc_html(
        *args, **kwargs,
        redoc_js_url='https://cdn.redoc.ly/redoc/latest/bundles/redoc.standalone.js',
    )


applications.get_swagger_ui_html = swagger_monkey_patch
applications.get_redoc_html = redoc_monkey_patch
app = FastAPI(title="AboutCareer")
```

### 1.配置文件
import config
app.config.from_object(config)
### 2.url_for（把视图函数转换为url）
```python
return url_for('login') 返回logi页面
```

### 3.视图函数传递参数
```python
@app.route('/my_list/<参数名称>')
def my_list(参数名称):
    return 'my_list{}'.format(参数名称)

```
传递参数类型；
string:接收任何没有\/的字符串(默认)
float：
int:
path：接收多少路径




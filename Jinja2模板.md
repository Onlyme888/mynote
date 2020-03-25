### 模板路径
1.默认在templates下查找文件
### 模板传参
1.模板在渲染是可以传递关键字参数，直接在html中使用{{参数名称}}接收
```python
render_template('index.html',username = 'alex')

```

2.如果自动参数过多，可以使用字典
```python    
contex = {
        'username':'知了课堂',
        'age':18,
        'country':'中国',
    }
    return
render_template('index.html',**contex)

```
### 模板中使用url_for
1.模板中使用url_for和视图函数中使用是基本一致，也是传递视图函数的名称
```python
<a href="{{ url_for('login') }}">登录</a>

```
### 过滤器
过滤器是通过（|）管道符使用的，例如{{name|length}} 将会返回name的长度，过滤器相当于一个函数，把当前的值传入，在根据过滤器的功能返回对应的值渲染到模板中，
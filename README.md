# نکات و ترفندهای پایتون

## <a name=''></a>فهرست

<!-- vscode-markdown-toc -->

- [فهرست](#)
- [نکات](#-1)
  - [تو JSON کلید (یا همون name) نمیتونه عدد (Integer) باشه](#JSONnameInteger)

<!-- vscode-markdown-toc-config
	numbering=false
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

## <a name='-1'></a>نکات

### <a name='JSONnameInteger'></a>تو JSON کلید (یا همون name) نمیتونه عدد (Integer) باشه

در JSON معمولا همه چیز به صورت name/value هست (یا همون key/value) و name نمیتونه عدد (Integer) باشه. name فقط و فقط باید string باشه و دورش " باشه.

حالا مثال زیر رو در نظر بگیرید:

```python
>>> import json
>>> a = {1:2}
>>> b = json.dumps(a)
>>> print(b)
{"1": 2}
>>> json.loads(b)
{'1': 2}
```

وقتی تو پایتون یک دیکشنری که کلید عددی داره رو json.dumps میکنیم بعدا اگر json.loads اش کنیم اون کلید عددی که تو دیکشنری داشتیم به عدد تبدیل نمیشه دوباره چون تو JSON کلید یا name عددی نداریم.

## ترفندها

### تبدیل دیکشنری به ابجکت Converting Dict to Object

راه های مختلفی وجود داره برای تبدیل دیکشنری به ابجکت ([راه های دیگه](https://stackoverflow.com/questions/1305532/how-to-convert-a-nested-python-dict-to-object))، راهی که من خوشم اومد ازش، استفاده از پکیج [munch](https://github.com/Infinidat/munch) هست.

```bash
pip install munch
```

نمونه کد استفاده ازش:

```python
>>> from munch import Munch
>>> d = {'a': 1, 'b': {'c': 2}, 'd': ["hi", {'foo': "bar"}]}
>>> obj = Munch.fromDict(d)
>>> obj.b.c
2
>>> obj.a
1
>>> obj.d[1].foo
'bar'
```

با استفاده از munchify(), Munch.fromDict() میشه راحت دیکشنری رو تبدیل به ابجکت کرد به صورت recursive (یعنی هر چی لییست و دیکشنری و غیره فرزند هم داخل دیکشنری مون باشه تبدیل به ابجکت میشه) و برای تبدیل ابجکت Munch به دیکشنری از unmunchify(), Munch.toDict() میشه استفاده کرد.

تو گیت هابش آموزش داده چطور از قابلیت های مختلفش استفاده کنید.

https://github.com/Infinidat/munch


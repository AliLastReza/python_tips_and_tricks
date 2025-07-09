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

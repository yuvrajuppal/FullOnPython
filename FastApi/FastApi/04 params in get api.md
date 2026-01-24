```python
@app.get('/product')
def productlist(limit):
return {
	"limit":limit
}
```

```
http://127.0.0.1:3000/product?limit=10
```

```python
@app.get('/product')
def productlist(limit,published):
return {
"limit":limit,
"published":published
}
```


```
http://127.0.0.1:3000/product?limit=10&published=True
```

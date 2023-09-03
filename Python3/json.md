this is what helps us use json files 

```
with open("whatever.json", 'r') as f:
	datastore = json.load(f)
```
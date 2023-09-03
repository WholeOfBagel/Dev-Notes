[Subword Tokenization](https://www.geeksforgeeks.org/subword-tokenization-in-nlp/#) is a good article to read on this topic

#### seeing associations in tensorflow:
```python
for ts in tokenized_string:
	print('{} -----> {}'.format(ts, tokenizer_subwords.decode([ts]) )
```


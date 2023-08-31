## Useful Methods
``` python
- `os.listdir(DIRECTORY)` returns a list with the contents of that directory.
    
- `os.path.getsize(PATH)` returns the size of the file
    
- `copyfile(source, destination)` copies a file from source to destination
    
- `random.sample(list, len(list))` shuffles a list
```

### Example Code
``` python
only_non_zero = [ ]
  for x in os.listdir(SOURCE_DIR):
    if os.path.getsize(os.path.join(SOURCE_DIR, x)) != 0:
      only_non_zero.append(x)
    else:
      print(x, 'is zero length, so ignoring')

  # if os.path.getsize(os.path.join(SOURCE_DIR, x)) !=0 else print(x, 'is zero length, so ignoring')
  full_size = len(only_non_zero)
  randomized = random.sample(only_non_zero, full_size)
  train_size = int(full_size * SPLIT_SIZE)
  
  for image in randomized[0:train_size]:
    # print(image)
    img_path = os.path.join(SOURCE_DIR, image)
    dir_path = os.path.join(TRAINING_DIR, image)
    copyfile(img_path, dir_path)
  for image in randomized[train_size:]:
    # print(image)
    img_path = os.path.join(SOURCE_DIR, image)
    dir_path = os.path.join(VALIDATION_DIR, image)
    copyfile(img_path, dir_path)
```
# Tensorflow-Sagemaker-deployment (Coursera Guided project)
Coursera project :- https://bit.ly/3kMcCcP

---

The images used in the following is downloaded from http://www.robots.ox.ac.uk/~vgg/data/pets/data/images.tar.gz
and the annotation are from http://www.robots.ox.ac.uk/~vgg/data/pets/data/annotations.tar.gz

---

All the files can be downloaded by running the following code

```python
    def download_and_extract(data_dir, download_dir):
    for url in urls:
        target_file = url.split('/')[-1]
        if target_file not in os.listdir(download_dir):
            print('Downloading', url)
            urllib.request.urlretrieve(url, os.path.join(download_dir, target_file))
            tf = tarfile.open(url.split('/')[-1])
            tf.extractall(data_dir)
        else:
            print('Already downloaded', url)
```


```python
    def get_annotations(file_path, annotations={}):
    
    with open(file_path, 'r') as f:
        rows = f.read().splitlines()

    for i, row in enumerate(rows):
        image_name, _, _, _ = row.split(' ')
        class_name = image_name.split('_')[:-1]
        class_name = '_'.join(class_name)
        image_name = image_name + '.jpg'
        
        annotations[image_name] = 'cat' if class_name[0] != class_name[0].lower() else 'dog'
    
    return annotations
```



```python
     if not os.path.isdir('data'):
        os.mkdir('data')
     download_and_extract('data', '.')
```

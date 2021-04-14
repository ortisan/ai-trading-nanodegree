# Content of Udacity AI for Trading Nanodegree

## Environment

```sh
conda create -n ai_trading python=3.6.3
conda activate ai_trading
pip install -r requirements.txt
```

## Start jupyter into folders

```sh
jupyter notebook <folder name>
```

## Get workspace of Udacity projects

### Copy folders

```python
import os
import shutil

zip_destination_folder = './zip'
shutil.rmtree(zip_destination_folder, ignore_errors=True)

#Copy source files
workspace_folder = os.path.join(os.getcwd())
shutil.copytree("./", zip_destination_folder)

#Copy data files
data_destination_folder = './zip/data'
data_folder = os.path.join(os.getcwd(), '..', '..', 'data')
shutil.copytree(data_folder, data_destination_folder)
```

### Zip workspace folder

```python
import os
import zipfile

def zipdir(path, ziph):
    # ziph is zipfile handle
    for root, dirs, files in os.walk(path):
        for file in files:
            ziph.write(os.path.join(root, file),
                       os.path.relpath(os.path.join(root, file),
                                       os.path.join(path, '..')))

zip_file = os.path.join(os.getcwd(), "workspace.zip")
zipf = zipfile.ZipFile(zip_file, 'w', zipfile.ZIP_DEFLATED)
zipdir(zip_destination_folder, zipf)
zipf.close()
```

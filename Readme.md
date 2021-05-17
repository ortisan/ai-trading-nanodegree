# Content of Udacity AI for Trading Nanodegree

## Concepts

- Time Series Modeling

  - [ARIMA Model](https://www.youtube.com/watch?v=3UmyHed0iYE)

  * [Kalman Filters](https://en.wikipedia.org/wiki/Kalman_filter#:~:text=In%20statistics%20and%20control%20theory,than%20those%20based%20on%20a)

- Portfolio Optmization

  - [Analysis of new approaches used in portfolio optimization: a systematic literature review - Paper](https://www.scielo.br/scielo.php?pid=S0103-65132020000100404&script=sci_arttext)

  * [cvxpy lib](https://www.cvxpy.org/)

- Factors

  - [Market Neutral Whitepaper](https://allaboutalpha.com/blog/wp-content/uploads/2011/03/A-Pared-Down-Approach-to-Stock-Picking-White-Paper.pdf)

  - [Factor Models](https://medium.com/wright-research/factor-models-744e17e5d0e5)

  - [Zipline doc](https://zipline-trader.readthedocs.io/en/latest/index.html)

## Environment

Install [Graphiz](https://graphviz.org/download/). This software is utilized to plot zipline pipeline graph.

```sh
sudo apt install graphviz
```

Install python environment.

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

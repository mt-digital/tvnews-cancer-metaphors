# tvnews-cancer-metaphors

Data scraping for cancer-related metaphors on the Internet Archive's TV News Archive.

## Install dependencies

Use a virtualenvironment for great good and install
[Metacorps](https://github.com/mtpain/metacorps) and 
[iatv](https://github.com/mtpain/iatv). 
These are a data model/web app for metaphor annotation of TV News
Archive data and a Python API for searching and scraping the TV News archive.

```
virtualenv venv && source venv/bin/activate && pip install -r requirements.txt
```

## Run data scraping and project building

This may not be too easy depending on your experience with Python. Please
open an issue or [email me](mailto:mturner8@ucmerced.edu) if you experience
difficulties. Some of these things might be easily fixed individually, but
have not been due to other higher priority work.

First, set up your environment, which connects the data model to specific
MongoDB collections by running 

```
export CONFIG_FILE="$PWD/venv/default.cfg"
```
in the terminal. This file was installed with Metacorps via `pip`.

To capture the data used in the Georgia talk, run `python
health_and_metaphor_getdata.py`. To review or analyze the metaphors and 
non-metaphors as annotated, run `python health_and_metaphor_analysis.py`.
Can't actually do that yet because these don't exist, but soon.

These scripts contain code that looks something like the following example.
Here I search for the term "breast cancer" on Fox News in 2017.

```python
from iatv import search_items
from app.model import Project  # actually Metacorps code; needs to be clarified

items = search_items(
    'breast+cancer', channel='FOXNEWSW', time='2017', rows=1000
)
```

`rows=1000` is included to avoid the default limit, which is only one or two
score.

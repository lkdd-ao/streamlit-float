streamlit-float  [![Version](https://img.shields.io/pypi/v/streamlit-float)](https://pypi.org/project/streamlit-float/#history) 
[![PyPi - Downloads](https://img.shields.io/pypi/dm/streamlit-float)](https://pypi.org/project/streamlit-float/#files)
============

Fix the vertical position of Streamlit containers relative to viewport instead of page

## Installation
Install [streamlit-float](https://pypi.org/project/streamlit-float/) with pip:
```bash
pip install streamlit-float
```

## Usage
This package provides two ways to float a container. The first is to call the `float` method of a container:

```python
import streamlit as st
from streamlit_float import *

# initialize float feature/capability
float_init()

col1, col2 = st.columns(2)

# Fix/float the whole column
col1.write("This entire column is fixed/floating")
col1.float()

with col2:
    container = st.container()
    # Fix/float a single container inside
    container.write("This text is in a container that is fixed")
    container.float()

```

Alternatively, you can use the `float_parent` method:

```python
import streamlit as st
from streamlit_float import *

# initialize float feature/capability
float_init()

col1, col2 = st.columns(2)

# Fix/float the whole column
with col1:
    st.write("This entire column is fixed/floating")
    float_parent()

with col2:
    container = st.container()
    # Fix/float a single container inside
    with container:
        st.write("This text is in a container that is fixed")
        float_parent()

```

Note that the float feature does not work well with `expander` and `tabs` containers. Also, it is recommended to call the float methods on a container after all the content has been added to it.

If instead you would like to float/fix a container that is constructed in html markup and added using Streamlits `markdown` method (with `unsafe_allow_html=True`), make sure to add 'floating' to the containers classlist.

```python
st.markdown('''<div class="floating">..content..</div>''', unsafe_allow_html=True)
```

## License
This project is licensed under the [MIT License](LICENSE.txt)
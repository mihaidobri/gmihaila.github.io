# **:computer: Useful Code**


:mag_right:  Here is where I put Python :snake: code snippets that I use in my Machine Learning :robot: research work. I'm using this page to have code easily accessible  and to be able to share it with others. 


:electric_plug: **Tip**: use **Table of contents** on the *top-right side of the page* to avoid endless scrolling, and is a good idea to use **Copy to clipboard** button on the *upper right corner of each code cell* to get things done quickly.

<br>


## **Read FIle**

One liner to read any file:

```python
io.open("my_file.txt", mode='r', encoding='utf-8').read()
```
**Details:** `import io`


## **Write File**

One liner to write a string to a file:

```python
io.open("my_file.txt", mode='w', encoding='utf-8').write("Your text!")
```
**Details:** `import io`


## **Debug**

Start debugging after this line: 
```python
import pdb; pdb.set_trace()
```
**Details:** use  `dir()` to see all current variables, `locals()` to see variables and their values and  `globals()` to see all global variables with values.


## **Pip Install GitHub**

Install library directly from GitHub using pip:
```bash
pip install git+github_url
```
**Details:** add `@version_number` at the end to use a certain version to install.


## **Parse Argument**
Parse arguments given when running a `.py` file.
```python
parser = argparse.ArgumentParser(description='Description')
parser.add_argument('--argument', help='Help me.', type=str)
# parse arguments
args = parser.parse_args()
```
**Details:** `import argparse` and use `python script.py --argument something` when running script.


## **Doctest**

How to run a simple unittesc using function documentaiton. Useful when need to do unittest inside notebook:
```python
# function to test
def add(a, b):
'''
>>> add(2, 2)
5
'''
return a + b
# run doctest
import doctest
doctest.testmod(verbose=True)
```
**Details:** [ml_things]()



## **Fix Text**

I use this package everytime I read text data from a source I don't trust. Since text data is always messy, I always use it. It is great in fixing any bad Unicode.

```python
fix_text(text="Text to be fixed")
```
**Details:** Install it `pip install ftfy` and import it `from ftfy import fix_text`.

## **Current Date**

How to get current date in Python. I use this when need to name log files:
```python
from datetime import date

today = date.today()

# dd/mm/YY in string format
today.strftime("%d/%m/%Y")
```
**Details:** More details [here](https://www.programiz.com/python-programming/datetime/current-datetime)


## **Current Time**

Get current time in Python:

```python
from datetime import datetime

# datetime object containing current date and time
now = datetime.now()

# dd/mm/YY H:M:S
now.strftime("%d/%m/%Y %H:%M:%S")
```
**Details:** More details [here](https://www.programiz.com/python-programming/datetime/current-datetime)


## **Remove Punctuation**

The fastest way to remove punctuation in Python3:

```python
table = str.maketrans(dict.fromkeys(string.punctuation))
"string. With. Punctuation?".translate(table) 
```
**Details:** Import `string`. Code adapted from StackOverflow [Remove punctuation from Unicode formatted strings](https://stackoverflow.com/questions/11066400/remove-punctuation-from-unicode-formatted-strings/11066687#11066687).


## **Class Instances from Dictionary**

Create class instances from dictionary. Very handy when working with notebooks and need to pass arguments as class instances.

```python
# Create dictionary of arguments.
my_args = dict(argument_one=23, argument_two=False)
# Convert dicitonary to class instances.
my_args = type('allMyArguments', (object,), my_args)
```

**Details:** Code adapted from StackOverflow [Creating class instance properties from a dictionary?](https://stackoverflow.com/a/1639215/11281368)


## **List of Lists into Flat List**

Given a list of lists convert it to a single flat size list. It is the fasest way to conserve each elemnt type.

```python
l = [[1,2,3],[4,5,6], [7], [8,9], ['this', 'is']]

functools.reduce(operator.concat, l)
```
**Details:** Import `operator, functools`. Code adapted from StackOverflow [How to make a flat list out of list of lists?](https://stackoverflow.com/a/45323085/11281368)


## **Pickle and Unpickle**

Save python objects into binary using pickle. Load python objects from binary files using pickle.

```python
a = {'hello': 'world'}

with open('filename.pickle', 'wb') as handle:
    pickle.dump(a, handle, protocol=pickle.HIGHEST_PROTOCOL)

with open('filename.pickle', 'rb') as handle:
    b = pickle.load(handle)
```
**Details:** Import `pickle`. Code adapted from StackOverflow [How can I use pickle to save a dict?](https://stackoverflow.com/a/11218504/11281368)

## **Notebook Input Variables**

How to ask user for input value to a variable. In the case of a password variable how to ask for a password variable.

```python
from getpass import getpass
# Populate variables from user inputs.
user = input('User name: ')
password = getpass('Password: ')
```
**Details:** Code adapted from StackOverflow [Methods for using Git with Google Colab](https://stackoverflow.com/a/57539179/11281368)


## **Notebook Private Repo Clone**

How to clone a private repo. Will need to login and ask for password. This snippet can be ran multiple times because it first check if the repo was cloned already.

```python
import os
from getpass import getpass
# Check if repo wasn't already cloned
if not os.path.isdir('/content/github_repo'):
  # Use GitHub username.
  u = 'github_username'
  # Ask user for GitHub password.
  p = getpass('GitHub password: ')
  # Clone repo.
  !git clone https://$u:$p@github.com/github_username/github_repo.git
  # Remove password variable.
  p = ''
```
**Details:** Code adapted from StackOverflow [Methods for using Git with Google Colab](https://stackoverflow.com/a/57539179/11281368)


## **Import Module Given Path**

How to import a module from a local path. Make it act as a installed library.

```python
import sys
# Append module path.
sys.path.append('/path/to/module')
```
**Details:** After that we can use `import module.stuff`. Code adapted from StackOverflow [Adding a path to sys.path (over using imp)](https://stackoverflow.com/a/129374/11281368).



## **PyTorch**

Code snippets related to [PyTorch](https://pytorch.org/docs/stable/index.html):

### **Dataset**

Code sample on how to create a PyTorch Dataset. The `__len__(self)` function needs to return the number of examples in your dataset and `_getitem__(self,item)` will use the index `item` to select an example from your dataset:

```python
from torch.utils.data import Dataset, DataLoader

class PyTorchDataset(Dataset):
  """PyTorch Dataset.
  """

  def __init__(self,):
    return

  def __len__(self):
    return 

  def __getitem__(self, item):
    return

# create pytorch dataset
pytorch_dataset = PyTorchDataset()
# move pytorch dataset into dataloader
pytorch_dataloader = DataLoader(pytorch_dataset, batch_size=32, shuffle=True)
```
**Details:** Find more details [here](https://pytorch.org/tutorials/beginner/data_loading_tutorial.html)


### **PyTorch Device**

How to setup `device` in PyTorch to detect if GPU is available. If there is no GPU available it will default to CPU.

```python
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
```
**Details:** Adapted from Stack Overflow [How to check if pytorch is using the GPU?](https://stackoverflow.com/questions/48152674/how-to-check-if-pytorch-is-using-the-gpu).

<br>

**TABLE OF CONTENTS**



# Python `venv`

`python3 -m venv .venv`

`source .venv/bin/activate`

`deactivate`

`which python3`

`pip install`

`python script.py`


# Find / Set Token Limits

```
ollama show gemma3filenames1:latest --verbose | grep "length"
```

Parameter  `PARAMETER num_ctx 1024` is expected to **always** overwrite any limits, and be taken on first.

# Tokens Count Script

```
import tiktoken

enc=tiktoken.get_encoding('cl100k_base')
text=open('token-counter-input.txt').read()
print('tokens:',len(enc.encode(text)))
```

**Images** may take between 100 and 500 tokens. For Gemma3, if I remember correctly, **270 tokens**.

# Experimental Determining of a Safe Token Limit for 5/8GB RAM

| num_ctx | RAM | Comment |
|:----|:---:|:---|
| 2048 | 4.01 | Looks to be stable |
| 4096 | 4.01 | Looks to be stable |
| 16384 | 4.32 | Looks to be trying to push over |
| 32768 | 5.37 | Looks to be trying to push over |
| unlim | 4.00 | Looks to be stable |

When OS runs out of memory, the laptop may crash and reboot.


# Syntax to include file and check

```
./images-001.jpeg
```

Expected output 

`Added image './image-001.jpeg'`

# Command(s) to test the prompt

```
ollama server

ollama pull # model to pul

ollama create {modelname} -f {path-to-model-file}

ollama run {modelname} "{prompt/input}"

ollama stop {modelname}

ollama rm {modelname}

ollama run {modelname} "Provide 10 names for this file ./image-001.jpeg"



```
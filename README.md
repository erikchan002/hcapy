# hcapy

hca2wav wrapper working on Python3.

## Summary

Python3 wrapper for [hca2wav](https://github.com/CrescentApricot/hca2wav) (forked [hca2wav](https://github.com/erikchan002/hca2wav)) which is an hca decoder based on [@Nyagamon](https://github.com/Nyagamon)'s [HCADecoder](https://github.com/Nyagamon/HCADecoder)<br>

## Dependencies
- Python3
- C++11

## Installation

```
pip3 install git+https://github.com/erikchan002/hcapy.git
```

## Usage

```python
import hcapy
import shutil

hcaDecoder = hcapy.Decoder(961961961961961)  # key

hcaDecoder.decode_file("target_file.hca", dest="decoded.wav")  # decode target_file.hca with the key above into decoded.wav

try:
  with open("target_file.hca", "rb") as f, open("decoded.wav", "wb") as f2:
    shutil.copyfileobj(hcaDecoder.decode(f.read()), f2) # decoding bytes into io.BytesIO
except hcapy.InvalidHCAError:
  print("invalid hca!")
```

### Key

The key can be a decimal integer `961961961961961`, or a hex string e.g. `"0x36ae63907b9e9"`, `"36ae63907b9e9"`,`"3907b9e9"`, `"36ae"`

### Output path

If `dest` is not specified the output path will be the same as the input file for `decode_file`



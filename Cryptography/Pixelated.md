# Pixelated
Category: Crypto
Points: 100
Author: Kaden Wu
## Problem Description
I have these 2 images, can you make a flag out of them? [scrambled1.png](https://mercury.picoctf.net/static/75e646e4ad19967ca1811f895fb40465/scrambled1.png)  [scrambled2.png](https://mercury.picoctf.net/static/75e646e4ad19967ca1811f895fb40465/scrambled2.png)
## Writeup
We can compose some code to add the two images together:
```python
import numpy as np
from PIL import Image
image1 = Image.open("scrambled1.png")
image2 = Image.open("scrambled2.png")
im1 = np.array(image1)
im2 = np.array(image2)
result = im1+im2
Image.fromarray(result).save('result.png')
```
After adding the two images together, we get this:![Preview](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQAAAAEACAIAAADTED8xAAADuUlEQVR4nO3Yy26CQABAUWz6/79MFybEzGh9tZV6z1npKAzRuSAe1nVdoOrj1QcAryQA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRA2uerD+A+h8NhWZZ1XV8y3fHpcWR7vI0Mb5g3eWbk7Ox/9jm8scPbf4jDSr1qWIXD57MNzq/OL/3Ug3mKS4fHvXZ6BThdtcPJdbnn3DkspmVaYbefTc+GdHbb7em8z8dGLs3O83Z9DzAs4ksn4+3xPHK6q3kPw8n1dJOzP34uLdZhw2HqeVf3jnyTmTCetOsAbjSv7Od3cnV5XZp02HBeu9uGpxelqyMzP4F+xDsEMJ90H3vPvZPe+J7jr6ztGjVfH66O8Ht2ehP8/T3ANv7APyrDns/eWpxuOO9ndstc8+Bj/wsNR77Pr+8f2XUALz+2nRzGbLcH9u/sOoDFd8wv22kA8Dfe4SYYHiYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0gRAmgBIEwBpAiBNAKQJgDQBkCYA0r4AA+83CIiYQeUAAAAASUVORK5CYII=)
Therefore, we have our flag!

`picoCTF{d562333d}`
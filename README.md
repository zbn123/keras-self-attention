# Keras Global Self-Attention

[![Travis](https://travis-ci.org/PoWWoP/keras-global-self-attention.svg)](https://travis-ci.org/PoWWoP/keras-global-self-attention)
[![Coverage](https://coveralls.io/repos/github/PoWWoP/keras-global-self-attention/badge.svg?branch=master)](https://coveralls.io/github/PoWWoP/keras-global-self-attention)


Attention mechanism for processing sequence data that considers the global context for each timestamp.

* ![](https://camo.githubusercontent.com/1ef0269557ea05b96b6894de202a109f6947dca6/687474703a2f2f6c617465782e636f6465636f67732e636f6d2f6769662e6c617465783f685f253742742c2673706163653b74272537442673706163653b3d2673706163653b25354374616e6828785f74253545542673706163653b575f742673706163653b2b2673706163653b785f2537427427253744253545542673706163653b575f782673706163653b2b2673706163653b625f7429)
* ![](https://camo.githubusercontent.com/f8c64f2abd4752037c50deb7373b55362d7c51dc/687474703a2f2f6c617465782e636f6465636f67732e636f6d2f6769662e6c617465783f655f253742742c2673706163653b74272537442673706163653b3d2673706163653b2535437369676d6128575f612673706163653b685f253742742c2673706163653b74272537442673706163653b2b2673706163653b625f6129)
* ![](https://camo.githubusercontent.com/c63a13424300fe05bee615ce051fece8b5bc1c9a/687474703a2f2f6c617465782e636f6465636f67732e636f6d2f6769662e6c617465783f615f253742742537442673706163653b3d2673706163653b25354374657874253742736f66746d617825374428655f7429)

## Install

```bash
pip install keras-global-self-attention
```

## Usage

```python
import keras
from keras_global_self_attention import Attention


model = keras.models.Sequential()
model.add(keras.layers.Embedding(input_dim=10000,
                                 output_dim=300,
                                 mask_zero=True))
model.add(keras.layers.Bidirectional(keras.layers.LSTM(units=128,
                                                       return_sequences=True)))
model.add(Attention())
model.add(keras.layers.Dense(units=5))
model.compile(
    optimizer='adam',
    loss='categorical_crossentropy',
    metrics=['categorical_accuracy'],
)
model.summary()
```

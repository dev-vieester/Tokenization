# Tokenization

A small, notebook-based exploration of text tokenization with a byte-level Byte Pair Encoding (BPE) tokenizer. The notebook trains a simple tokenizer on the Tiny Shakespeare text dataset, then demonstrates how frequent adjacent byte pairs can be merged into larger tokens.

## Repository contents

- [`tokenization.ipynb`](./tokenization.ipynb) — downloads the sample training text, defines `BasicTokenizer` with training, encoding, and decoding methods, and trains it with a vocabulary size of 1,000.

## Getting started

### Requirements

- Python 3
- Jupyter Notebook or Google Colab
- Python packages `requests` and `regex`

Install the packages locally if needed:

```bash
python -m pip install requests regex notebook
```

### Run the notebook

1. Clone or download this repository.
2. Start Jupyter and open `tokenization.ipynb`, or upload the notebook to Google Colab.
3. Run the cells from top to bottom. The first cell downloads the Tiny Shakespeare text and saves it as `training.txt` in the notebook's working directory.

The notebook trains the tokenizer using a vocabulary size of 1,000. Adjust the value passed to `tokenizer.train(text, 1000)` to experiment with a different vocabulary size.

## How it works

`BasicTokenizer` starts with UTF-8 byte values as tokens. During training, it repeatedly finds the most frequent adjacent pair and merges it into a new token. `encode` applies the learned merges to text, while `decode` reconstructs text from token IDs. The notebook also defines a GPT-style pre-tokenization pattern for exploration.

## Notes

- The training text is downloaded from the Tiny Shakespeare dataset hosted by [karpathy/char-rnn](https://github.com/karpathy/char-rnn).
- This is an educational example, not a production-ready tokenizer. The learned merges are held in memory and are not saved as a reusable model file.

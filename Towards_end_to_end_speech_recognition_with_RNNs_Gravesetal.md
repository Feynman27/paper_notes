# Towards End-to-End Speech Recognition with Recurrent Neural Networks
**Pdf link**: http://www.jmlr.org/proceedings/papers/v32/graves14.pdf
## Introduction
- Speech recognition system that transcribes audio data to text. 
- Uses spectrograms with deep bidirectional LSTM network
- Other methods for speech recognition involve training neural networks to classify invidual frames of acoustic data and reformulate the output distributions as emission probabilities in a Hidden Markov Model (HMM).
    - Requires network training to be alternated with HMM re-alignments to generate more accurate models.
    - Requires human effort to create pronunciation dictionaries to map words to phoneme sequences.
- Goal of the paper: Use a single end-to-end RNN to generate text from speech
    - Use spectrograms with a deep bidirectional LSTM network with Connectionist Temporal Classification (CTC)
- CTC integrates over all possible input-output alignment, and thus requires no re-alignment as is required in HMM network.
- Objective function directly optimizes word-error rate.

## Network Architecture
Recurrent neural networks take an input sequence $$\bf{x} = (x_{1}...x_{T})$$, computes a hidden vector $\bf{h} = (h_{1}...h_{T})$ and outputs a vector sequence $\bf{y} = (y_{1}...y_{T})$ by iterating from $t=1$ to $T$:

\begin{equation}

  h_{t} = H(W_{ih}x_{t} + W_{hh}h_{t-1} + b_{h})
  y_{t} = W_{h_{0}h_{t}} + b_{0}
\end{equation}

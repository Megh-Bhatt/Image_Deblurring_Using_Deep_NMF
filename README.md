# Image_Deblurring_Using_Deep_NMF

Deep NMF uses a multi-layer approach where the factorization occurs in several layers,
similar to deep learning models. Instead of directly factorizing V into W and H, we
decompose V through intermediate layers of factorization:
#### V ≈ W1 · W2 · · · · · Wk · H

Here, each Wi represents a layer of decomposition, and the deeper structure allows for
capturing more complex representations of the data.

# CTR

CTR模式也称为计数器模式，每个分组对应一个累加的计数器，并通过计数器来生成加密密钥流。

<img src="/assets/1202px-CTR_encryption_2.svg.png" width="600">

图中Nonce+Counter是一个计数器，Nonce和前面几种模式的IV类似，每次加密都需要随机生成。而计数器Counter是累加的。

CTR模式特点是每组加密都是独立的，不依赖前一组，这就意味着在生成计数器后，每个分组可以并行计算。
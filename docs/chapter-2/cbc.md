#CBC

CBC模式由IBM发明与1976年，在CBC模式中，每个平文块先与前一个密文块进行异或后，再进行加密。在这种方法中，每个密文块都依赖于它前面的所有平文块。同时，为了保证每条消息的唯一性，在第一个块中需要使用初始化向量。

<img src="/assets/1202px-CBC_encryption.svg.png" width="600">

这里引入了初始化向量IV，因为第一组明文不存在"前一个密文"，一般来说每次加密都会生成随机值来做初始
化向量。
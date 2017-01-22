# **Diffie-Hellman密钥交换**

[迪菲-赫尔曼密钥交换](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)（Diffie–Hellman key exchange）是一种安全协议。它可以让双方在完全没有对方任何预先信息的条件下通过不安全信道创建起一个密钥。公钥交换的概念最早由瑞夫·墨克（Ralph C. Merkle）提出，而这个密钥交换方法，由惠特菲尔德·迪菲（Bailey Whitfield Diffie）和马丁·赫尔曼（Martin Edward Hellman）在1976年首次发表。

DH加密算法也是基于一数学难题：[离散对数问题](https://en.wikipedia.org/wiki/Discrete_logarithm)。简单的说，A=g^a \(mod p\),  已知g,a,p 求A容易，但从已知的A, g, p，很难求得a。

## 密钥交换过程

![](/assets/dh.png)








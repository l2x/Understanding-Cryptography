# **Diffie-Hellman密钥交换**

[迪菲-赫尔曼密钥交换](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)（Diffie–Hellman key exchange）是一种安全协议。它可以让双方在完全没有对方任何预先信息的条件下通过不安全信道创建起一个密钥。公钥交换的概念最早由瑞夫·墨克（Ralph C. Merkle）提出，而这个密钥交换方法，由惠特菲尔德·迪菲（Bailey Whitfield Diffie）和马丁·赫尔曼（Martin Edward Hellman）在1976年首次发表。

DH加密算法也是基于一数学难题：[离散对数问题](https://en.wikipedia.org/wiki/Discrete_logarithm)。简单的说，A=g^a \(mod p\),  已知g,a,p 求A容易，但从已知的A, g, p，很难求得a。

## 密钥交换过程

![](/assets/dh.png)

DH密钥交换并没有交换任何"密钥"，而是通过交换数据最终双方能够生成同样的密钥。

假设作为一名攻击者，截获双方的数据并尝试进行破解，拿上例来说，尝试对Bob数据进行破解：

1. s = A ^ b % p，A和p已知，想获取到密钥s，必须知道b。
2. B = g ^ b % p，B和g，p已知，但离散对数问题说明了b很难被破解。




# RC4

[RC4（来自Rivest Cipher 4）](https://en.wikipedia.org/wiki/RC4)由美国密码学家罗纳德·李维斯特（Ron Rivest）在1987年设计，是一种流加密算法，密钥长度可变。它加解密使用相同的密钥，因此也属于对称加密算法。RC4是有线等效加密（WEP）中采用的加密算法，也曾经是TLS可采用的算法之一。由于RC4算法存在弱点，2015年2月所发布的 [RFC 7465](https://tools.ietf.org/html/rfc7465) 规定禁止在TLS中使用RC4加密算法。

## 算法

总结起来就3步：  
1. 通过算法生成一个255字节的S-box。  
2. 再通过算法每次取出S-box中的某一字节K.  
3. 将K与明文做异或得到密文。

**Step1. 密钥变换算法**

```
for i from 0 to 255
    S[i] := i
endfor
j := 0
for i from 0 to 255
    j := (j + S[i] + key[i mod keylength]) mod 256
    swap values of S[i] and S[j]
endfor
```

先初始化S-box，使得S\[0\] = 0, S\[1\] = 1 ... S\[254\] = 254。  
而后再打乱S-box，这一步会引入密钥。打乱后得到一个乱序的S-box。

**Step2. 伪随机算法**

```
i := 0
j := 0
while GeneratingOutput:
    i := (i + 1) mod 256
    j := (j + S[i]) mod 256
    swap values of S[i] and S[j]
    K := S[(S[i] + S[j]) mod 256]
    output K
endwhile
```

通过算法取出S-box中的一位K。

**Step3. 加密**

将上一步取出的K与明文当前字节做异或得到密文。明文的每一字节都会重复2，3步骤。

## 安全性




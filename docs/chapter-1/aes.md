# AES

[AES（Advanced Encryption Standard）](https://zh.wikipedia.org/wiki/%E9%AB%98%E7%BA%A7%E5%8A%A0%E5%AF%86%E6%A0%87%E5%87%86)，在密码学中又称Rijndael加密法，是美国联邦政府采用的一种区块加密标准。这个标准用来替代原先的DES。其密钥长度则可以是128，192或256比特。

> AES选定过程
>
> 1997年2月，[美国国家标准与技术研究院](https://zh.wikipedia.org/wiki/%E7%BE%8E%E5%9B%BD%E5%9B%BD%E5%AE%B6%E6%A0%87%E5%87%86%E4%B8%8E%E6%8A%80%E6%9C%AF%E7%A0%94%E7%A9%B6%E9%99%A2)（NIST）宣布希望选出一种新的加密算法用于替代DES。数月后15种加密算法被提交，分别是：[CAST-256](https://en.wikipedia.org/wiki/CAST-256),[CRYPTON](https://en.wikipedia.org/wiki/CRYPTON),[DEAL](https://en.wikipedia.org/wiki/DEAL),[DFC](https://en.wikipedia.org/wiki/DFC_(cipher),[E2](https://en.wikipedia.org/wiki/E2_(cipher),[FROG](https://en.wikipedia.org/wiki/FROG),[HPC](https://en.wikipedia.org/wiki/Hasty_Pudding_cipher),[LOKI97](https://en.wikipedia.org/wiki/LOKI97),[MAGENTA](https://en.wikipedia.org/wiki/MAGENTA),[MARS](https://en.wikipedia.org/wiki/MARS_(cryptography),[RC6](https://en.wikipedia.org/wiki/RC6),[Rijndael](https://en.wikipedia.org/wiki/Rijndael),[SAFER+](https://en.wikipedia.org/wiki/SAFER),[Serpent](https://en.wikipedia.org/wiki/Serpent_(cipher),[Twofish](https://en.wikipedia.org/wiki/Twofish)。
>
> 经过数轮的讨论与筛选，最终5种算法进入最终轮：[MARS](https://en.wikipedia.org/wiki/MARS_(cryptography),[RC6](https://en.wikipedia.org/wiki/RC6),[Rijndael](https://en.wikipedia.org/wiki/Rijndael),[Serpent](https://en.wikipedia.org/wiki/Serpent_(cipher), [Twofish](https://en.wikipedia.org/wiki/Twofish)。最后经过专家投票，Rijndael胜出，成为了AES标准。
>
> [Rijndael](https://en.wikipedia.org/wiki/Rijndael): 86 positive, 10 negative  
> [Serpent](https://en.wikipedia.org/wiki/Serpent_(cipher): 59 positive, 7 negative  
> [Twofish](https://en.wikipedia.org/wiki/Twofish): 31 positive, 21 negative  
> [RC6](https://en.wikipedia.org/wiki/RC6): 23 positive, 37 negative  
> [MARS](https://en.wikipedia.org/wiki/MARS_(cryptography)：13 positive, 84 negative

## 算法

<img src="/assets/aes-round.png" width="600">

1. **SubBytes**：通过一个非线性的替换函数，用查找表(S-Box)的方式把每个字节替换成对应的字节。
2. **ShiftRows**：将矩阵中的每个横列进行循环式移位。
3. **MixColumns**：每一列的四个字节通过线性变换互相结合得到新的4字节值.
4. **AddRoundKey**：将输入与**轮密钥**进行XOR。

以上就是AES加密中的一轮，不同密钥长度进行的轮数不同，128位10轮，192位12轮，256位14轮。

下面具体分析每一步：

**SubBytes**

从一张拥有256个值的替换表(S-Box)中找出对应的值替换。S-Box是固定的，查找公式也是固定。具体可参见[Rijndael S-box](https://en.wikipedia.org/wiki/Rijndael_S-box)。用此步骤混淆了输入内容。

**ShiftRows**

上一步处理后将16个字节分为4组，每组4字节。以字节位单位进行乱序处理，这种打乱是有规律的。如上图中输入第一组第一个字节移动到输出第一组第一个字节，输入第一组第二个字节移动到输入第二组第二个字节，输入第一组第三个字节移动到输出第三组第三个字节。

**MixColumns**

可以理解为采用固定的公式，将每组4个字节做运算得出另外4个字节。具体可参见[Rijndael mix columns](https://en.wikipedia.org/wiki/Rijndael_mix_columns)。

**AddRoundKey**

与轮密钥做异或。

**轮密钥**

轮密钥是通过密钥编排得到：将原始输入的密钥（128位、192位、256位）作为输入，得到子密钥。

<img src="/assets/aes-128-key-schedule.png" width="600">



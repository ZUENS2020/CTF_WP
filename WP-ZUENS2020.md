# CTF WP (ZUENS2020)


## 安全杂项
- Misc入门指北 - 50 pts ✅
    - 附件PDF中的隐藏字段
- ez_LSB - 50 pts ✅
    - 使用StegSolve
    ![StegSolve]
- SSTV - 100 pts ✅
    ![SSTV]
- 掐住一只耳 - 100 pts ✅
    - 使用Audacity可以发现左声道的摩斯电码
    ![moss]
- Enchantment - 150 pts ✅
    - 使用tshark从enchantment.pcapng中找出图片-AI
    ![SGA]
    - 解开SGA银河字母[https://www.dcode.fr/standard-galactic-alphabet]
- ez_png - 200 pts ✅
    - 理解 PNG 文件结构:    -AI
       PNG 格式由一连串 chunk（数据块）组成，每个 chunk 包括：
      | 4字节长度 | 4字节块类型 | 数据区 | 4字节CRC |
      常见的块类型：
        IHDR：文件头信息（宽度、高度、颜色类型等）
        IDAT：图像压缩数据，可有多个
        IEND：文件尾标识
    - 使用工具查看chunk[https://www.nayuki.io/page/png-file-chunk-inspector]
    - 发现可疑块
    ![chunk]
    - 解码899 007部分 -AI
    ![Zlib]

## 从此开始
- 签到 - 50 pts ✅

## 二进制漏洞审计
- 0 二进制漏洞审计入门指北 - 100 pts ✅
- 1 ez_u64 - 100 pts ✅
- 2 EZtext - 100 pts
- fmt - 150 pts
- randomlock - 150 pts
- str_check - 150 pts
- syslock - 150 pts
- easylibc - 200 pts
- fmt_S - 250 pts

## 密码学
- Crypto入门指北 - 50 pts ✅
- ez_DES - 50 pts ✅
- baby_next - 100 pts ✅
- ez_square - 100 pts ✅
- ezlegendre - 150 pts ✅

## 逆向工程
- 逆向工程入门指北 - 50 pts
- upx - 100 pts
- ez3 - 150 pts
- flower - 150 pts
- A cup of tea - 200 pts
- mazegame - 200 pts

## Web安全与渗透测试
- 0 Web入门指北 - 50 pts ✅
- 01 第一章 神秘的手镯 - 50 pts ✅
- 02 第二章 初识金曜玄轨 - 50 pts ✅
- 03 第三章 向剑石！算天攻击! - 50 pts ✅
- 05 第五章 打上门来! - 50 pts ✅
- Moe笑传之猜猜爆 - 50 pts ✅
- 04 第四章 金曜极禁与七绝伶俐阵 - 100 pts
- 06 第六章 藏经禁地？玄机初探! - 100 pts
- 07 第七章 灵媒妖穴与阴阳双生符 - 150 pts
- 08 第八章 天行真言，星图显圣 - 200 pts



[StegSolve]:https://cdn.luogu.com.cn/upload/image_hosting/edtwi6vn.png?x-oss-process=image/resize,m_lfit,h_170,w_225

[SSTV]:https://cdn.luogu.com.cn/upload/image_hosting/u4kcc7iv.png

[moss]:https://cdn.luogu.com.cn/upload/image_hosting/2k7ni7yn.png?x-oss-process=image/resize,m_lfit,h_170,w_225

[SGA]:https://cdn.luogu.com.cn/upload/image_hosting/082kb65a.png?x-oss-process=image/resize,m_lfit,h_170,w_225

[chunk]:https://cdn.luogu.com.cn/upload/image_hosting/bw3glndu.png?x-oss-process=image/resize,m_lfit,h_170,w_225

[Zlib]:https://cdn.luogu.com.cn/upload/image_hosting/s1by0js1.png?x-oss-process=image/resize,m_lfit,h_170,w_225
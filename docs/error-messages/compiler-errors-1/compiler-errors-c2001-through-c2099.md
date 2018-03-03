---
title: "编译器错误 C2000 到 C2099 |Microsoft 文档"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
helpviewer_keywords:
- C2000
- C2016
- C2023
- C2024
- C2025
- C2029
- C2031
- C2035
- C2037
- C2038
- C2049
- C2068
- C2076
- C2080
- C2096
- C2098
dev_langs:
- C++
ms.assetid: d99a19eb-eeeb-4181-9b33-9cbe4459767b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8575e067f376f98c8312496b74bd05ba3d9bfce1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c2000-through-c2099"></a>编译器错误 C2000 到 C2099

本部分中的文档的文章说明由编译器生成的错误消息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>错误消息

|Error|消息|
|-----------|-------------|
|编译器错误 C2000|请未知错误，选择技术支持命令的 Visual c + + 帮助菜单上，或打开技术支持帮助文件了解详细信息|
|[编译器错误 C2001](compiler-error-c2001.md)|常量中有换行符|
|[编译器错误 C2002](compiler-error-c2002.md)|无效的宽字符常量|
|[编译器错误 C2003](compiler-error-c2003.md)|预期定义的 id|
|[编译器错误 C2004](compiler-error-c2004.md)|应输入“defined(id)”|
|[编译器错误 C2005](compiler-error-c2005.md)|#line 应为行号，却找到*令牌*|
|[编译器错误 C2006](compiler-error-c2006.md)|*指令*： 应为文件名，找到*令牌*|
|[编译器错误 C2007](compiler-error-c2007.md)|#define 语法|
|[编译器错误 C2008](compiler-error-c2008.md)|*字符*： 宏定义中的意外|
|[编译器错误 C2009](compiler-error-c2009.md)|重复使用的宏形式*标识符*|
|[编译器错误 C2010](compiler-error-c2010.md)|*字符*： 意外宏形参表中|
|[编译器错误 C2011](compiler-error-c2011.md)|*标识符*:*类型*类型重定义|
|[编译器错误 C2012](compiler-error-c2012.md)|在“<”之后缺少名称|
|[编译器错误 C2013](compiler-error-c2013.md)|缺少“>”|
|[编译器错误 C2014](compiler-error-c2014.md)|预处理器命令必须作为第一个非空白空间启动|
|[编译器错误 C2015](compiler-error-c2015.md)|常量中的字符太多|
|编译器错误 C2016|C 要求结构或联合具有至少一个成员|
|[编译器错误 C2017](compiler-error-c2017.md)|非法的转义序列|
|[编译器错误 C2018](compiler-error-c2018.md)|未知的字符"0 x*值*|
|[编译器错误 C2019](compiler-error-c2019.md)|预期的预处理器指令，却找到*字符*|
|[编译器错误 C2020](compiler-error-c2020.md)|*成员*:*类*成员重定义|
|[编译器错误 C2021](compiler-error-c2021.md)|不需要指数值，但*字符*|
|[编译器错误 C2022](compiler-error-c2022.md)|*数*： 对字符来说太大|
|编译器错误 C2023|*标识符*： 对齐方式 (*number1*) 不同于以前的声明 (*number2*)|
|编译器错误 C2024|alignas 特性应用于变量、 数据成员和仅适用于标记类型|
|编译器错误 C2025|无效或已损坏的二进制模块接口文件:*filename*|
|[编译器错误 C2026](compiler-error-c2026.md)|字符串太大，已截断尾部字符|
|[编译器错误 C2027](compiler-error-c2027.md)|使用未定义的类型*类型*|
|[编译器错误 C2028](compiler-error-c2028.md)|结构/联合成员必须在结构/联合中|
|编译器错误 C2029|左侧的*令牌*指定未定义的类/结构/接口*标识符*|
|[编译器错误 C2030](compiler-error-c2030.md)|具有“protected private”可访问性的析构函数不能是声明为“sealed”的类的成员|
|编译器错误 C2031|使用虚拟的析构函数*可访问性*对于此类型不允许可访问性|
|[编译器错误 C2032](compiler-error-c2032.md)|*标识符*： 函数不能为结构/联合的成员*类型*|
|[编译器错误 C2033](compiler-error-c2033.md)|*标识符*： 位域不能有间接寻址|
|[编译器错误 C2034](compiler-error-c2034.md)|*标识符*： 位域的比特数太小的类型|
|编译器错误 C2035|与非虚拟的析构函数*可访问性*对于此类型不允许可访问性|
|[编译器错误 C2036](compiler-error-c2036.md)|*标识符*': 未知的大小|
|编译器错误 C2037|左侧的*标识符*指定未定义的结构/联合*类型*|
|编译器错误 C2038|无法以内联方式 std 命名空间中。|
|[编译器错误 C2039](compiler-error-c2039.md)|*identifier1*： 不是成员的*identifier2*|
|[编译器错误 C2040](compiler-error-c2040.md)|*运算符*:*identifier1*在与的间接级别不同*identifier2*|
|[编译器错误 C2041](compiler-error-c2041.md)|非法数字*字符*for base'*数*|
|[编译器错误 C2042](compiler-error-c2042.md)|signed/unsigned 关键字互相排斥|
|[编译器错误 C2043](compiler-error-c2043.md)|非法 break|
|[编译器错误 C2044](compiler-error-c2044.md)|非法 continue|
|[编译器错误 C2045](compiler-error-c2045.md)|*标识符*： 标签被重定义|
|[编译器错误 C2046](compiler-error-c2046.md)|非法的 case|
|[编译器错误 C2047](compiler-error-c2047.md)|非法的 default|
|[编译器错误 C2048](compiler-error-c2048.md)|default 多于一个|
|编译器错误 C2049|*标识符*： 非内联命名空间无法重新打开为内联|
|[编译器错误 C2050](compiler-error-c2050.md)|switch 表达式不整型|
|[编译器错误 C2051](compiler-error-c2051.md)|case 表达式不是常量|
|[编译器错误 C2052](compiler-error-c2052.md)|*类型*： 非法的 case 表达式类型|
|[编译器错误 C2053](compiler-error-c2053.md)|*标识符*： 宽字符串不匹配|
|[编译器错误 C2054](compiler-error-c2054.md)|预期 (遵循*标识符*|
|[编译器错误 C2055](compiler-error-c2055.md)|预期的形式参数列表中，不是类型列表|
|[编译器错误 C2056](compiler-error-c2056.md)|非法表达式|
|[编译器错误 C2057](compiler-error-c2057.md)|应输入常量表达式|
|[编译器错误 C2058](compiler-error-c2058.md)|常量表达式不是整型|
|[编译器错误 C2059](compiler-error-c2059.md)|语法错误:*令牌*|
|[编译器错误 C2060](compiler-error-c2060.md)|语法错误： 发现文件尾|
|[编译器错误 C2061](compiler-error-c2061.md)|语法错误： 标识符 '*标识符*|
|[编译器错误 C2062](compiler-error-c2062.md)|类型*类型*意外|
|[编译器错误 C2063](compiler-error-c2063.md)|*标识符*： 不是函数|
|[编译器错误 C2064](compiler-error-c2064.md)|项不会计算为函数拍摄*数*自变量|
|[编译器错误 C2065](compiler-error-c2065.md)|*标识符*： 未声明的标识符|
|[编译器错误 C2066](compiler-error-c2066.md)|强制转换为函数类型是非法的|
|[编译器错误 C2067](compiler-error-c2067.md)|转换到数组类型是非法的|
|编译器错误 C2068|重载函数的非法使用。 缺少自变量列表？|
|[编译器错误 C2069](compiler-error-c2069.md)|“void”项到非“void”项的转换|
|[编译器错误 C2070](compiler-error-c2070.md)|*类型*： 非法的 sizeof 操作数|
|[编译器错误 C2071](compiler-error-c2071.md)|*标识符*： 非法存储类|
|[编译器错误 C2072](compiler-error-c2072.md)|*标识符*： 函数的初始化|
|[编译器错误 C2073](compiler-error-c2073.md)|*标识符*： 部分初始化数组的元素必须具有默认构造函数|
|[编译器错误 C2074](compiler-error-c2074.md)|*标识符*:*类型*初始化需要大括号括初始值设定项列表|
|[编译器错误 C2075](compiler-error-c2075.md)|*标识符*： 数组初始化需要大括号括初始值设定项列表|
|编译器错误 C2076|大括号括初始值设定项列表不能在一个新的表达式的类型包含*类型*|
|[编译器错误 C2077](compiler-error-c2077.md)|非标量字段初始值设定项*标识符*|
|[编译器错误 C2078](compiler-error-c2078.md)|初始值设定项太多|
|[编译器错误 C2079](compiler-error-c2079.md)|*标识符*使用未定义的结构/类/联合*类型*|
|编译器错误 C2080|*标识符*: 类型 '*类型*仅能从单个初始值设定项表达式中推导|
|[编译器错误 C2081](compiler-error-c2081.md)|*标识符*： 形参列表非法中的名称|
|[编译器错误 C2082](compiler-error-c2082.md)|正式参数重新定义*标识符*|
|[编译器错误 C2083](compiler-error-c2083.md)|结构/联合比较非法|
|[编译器错误 C2084](compiler-error-c2084.md)|函数*标识符*已具有一个主体|
|[编译器错误 C2085](compiler-error-c2085.md)|*标识符*： 形参列表中没有|
|[编译器错误 C2086](compiler-error-c2086.md)|*标识符*： 重定义|
|[编译器错误 C2087](compiler-error-c2087.md)|*标识符*： 缺少下标|
|[编译器错误 C2088](compiler-error-c2088.md)|*运算符*： 非法的结构/类/联合|
|[编译器错误 C2089](compiler-error-c2089.md)|*标识符*:*类型*太大|
|[编译器错误 C2090](compiler-error-c2090.md)|函数返回数组|
|[编译器错误 C2091](compiler-error-c2091.md)|函数返回函数|
|[编译器错误 C2092](compiler-error-c2092.md)|*标识符*数组元素类型不能是函数|
|[编译器错误 C2093](compiler-error-c2093.md)|*identifier1*： 无法使用自动变量的地址初始化*identifier2*|
|[编译器错误 C2094](compiler-error-c2094.md)|标签*标识符*未定义|
|[编译器错误 C2095](compiler-error-c2095.md)|*函数*： 实参具有类型 void： 参数*数*|
|编译器错误 C2096|*标识符*： 不能用一个用圆括号括起来初始值设定项初始化的数据成员|
|[编译器错误 C2097](compiler-error-c2097.md)|初始化非法|
|编译器错误 C2098|数据成员后的出现意外的标记*标识符*|
|[编译器错误 C2099](compiler-error-c2099.md)|初始值设定项不是常量|

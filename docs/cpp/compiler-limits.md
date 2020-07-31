---
title: 编译器限制
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: e0e2381d88c727466b06a97c72826d2d5e15a87b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233764"
---
# <a name="compiler-limits"></a>编译器限制

C++ 标准建议对各种语言构造施加限制。 下面列出了 Microsoft c + + 编译器未实现建议的限制的情况。 第一个数字是在 ISO c + + 11 标准（INCITS/ISO/IEC 14882-2011 [2012]，附录 B）中建立的限制，第二个数字是 Microsoft c + + 编译器实现的限制：

- 复合语句、迭代控制结构和选择控制结构的嵌套级别-c + + 标准：256，Microsoft c + + 编译器：依赖于嵌套的语句的组合，但通常介于100和110之间。

- 一个宏定义中的参数-c + + 标准：256，Microsoft c + + 编译器：127。

- 一个宏调用中的参数-c + + 标准：256，Microsoft c + + 编译器127。

- 字符串文本或宽字符串文本中的字符（串联后）-c + + 标准：65536，Microsoft c + + 编译器：65535单字节字符（包括 NULL 终止符）和32767双字节字符，包括 NULL 结束符。

- 单个 c + + 标准中的嵌套类、结构或联合定义的级别 `struct-declaration-list` ：256，Microsoft c + + 编译器：16。

- 构造函数定义中的成员初始值设定项-c + + 标准：6144，Microsoft c + + 编译器：至少为6144。

- 一个标识符的范围限定-c + + 标准：256，Microsoft c + + 编译器：127。

- 嵌套 **`extern`** 规范-c + + 标准：1024，Microsoft c + + 编译器：9（不计算全局范围内的隐式 **`extern`** 规范，如果您在全局范围内统计隐式规范，则不计算10）。 **`extern`**

- 模板声明中的模板参数-c + + 标准：1024，Microsoft c + + 编译器：2046。

## <a name="see-also"></a>另请参阅

[非标准行为](../cpp/nonstandard-behavior.md)

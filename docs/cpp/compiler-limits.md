---
title: 编译器限制
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9663da06c97886ef1cd20ca2928944795b39dc18
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222204"
---
# <a name="compiler-limits"></a>编译器限制

C++ 标准建议对各种语言构造施加限制。 以下是列表的情况下，MicrosoftC++编译器不实现建议的限制。 第一个数字是 ISO 中建立的限制C++11 标准 (INCITS/ISO/IEC 14882-2011 [2012]，附件 B) 和第二个数字是由 Microsoft 实现的限制C++编译器：

- 嵌套级别的复合语句、 迭代控制结构和选择控制结构的C++标准：256，MicrosoftC++编译器： 取决于组合的语句嵌套的但通常介于 100 和 110 之间。

- 一个宏定义-中的参数C++标准：256，MicrosoftC++编译器：127.

- 一个宏调用-中的参数C++标准：256，MicrosoftC++编译器： 127。

- 中的字符 （串联后） 的字符串文本或宽字符串文本C++标准：65536，MicrosoftC++编译器：65535 的单字节字符，包括 NULL 终止符，并包括 NULL 终止符的 32767 双字节字符。

- 级别的嵌套的类、 结构或联合定义中单个`struct-declaration-list`-C++标准：256，MicrosoftC++编译器：16。

- 成员初始值设定项中的构造函数定义的C++标准：6144，MicrosoftC++编译器： 至少为 6144。

- 一个标识符的范围限定C++标准：256，MicrosoftC++编译器：127.

- 嵌套**extern**规范的C++标准：1024，MicrosoftC++编译器：9 (不包括的隐式**extern**规范在全局作用域或 10，如果您要计算的隐式**extern**全局作用域中的规范...

- 模板声明-中的模板自变量C++标准：1024，MicrosoftC++编译器：2046.

## <a name="see-also"></a>请参阅

[非标准行为](../cpp/nonstandard-behavior.md)
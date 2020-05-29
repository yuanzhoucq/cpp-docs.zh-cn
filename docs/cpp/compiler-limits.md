---
title: 编译器限制
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9e61cae1638c87f03b6fa775552408961bde6859
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189569"
---
# <a name="compiler-limits"></a>编译器限制

C++ 标准建议对各种语言构造施加限制。 下面列出了 Microsoft C++编译器未实现建议限制的情况。 第一个数字是在 ISO C++ 11 标准（INCITS/ISO/IEC 14882-2011 [2012]，附录 B）中建立的限制，第二个数字是由 Microsoft C++编译器实现的限制：

- 复合语句、迭代控制结构和选择控制结构的嵌套级别- C++标准：256，Microsoft C++编译器：取决于嵌套的语句的组合，但通常介于100和110之间。

- 一个宏定义中的参数- C++标准：256，Microsoft C++编译器：127。

- 一个宏调用中的参数C++ -标准：256， C++ Microsoft 编译器127。

- 字符串文本或宽字符串文本中的字符（串联后）- C++标准：65536，Microsoft C++编译器：65535单字节字符（包括 null 终止符）和32767双字节字符，包括 null 结束符。

- 单个 `struct-declaration-list` C++标准：256，Microsoft C++编译器：16中的嵌套类、结构或联合定义的级别。

- 构造函数定义中的成员初始值C++设定项-标准： C++ 6144，Microsoft 编译器：至少为6144。

- 一个标识符C++标准：256，Microsoft C++编译器：127的范围限定。

- 嵌套**extern**规范- C++标准：1024，Microsoft C++编译器：9（不计算全局范围内的隐式**extern**规范，或10，如果在全局范围内对隐式**extern**规范进行计数。

- 模板声明中的模板参数- C++标准：1024，Microsoft C++编译器：2046。

## <a name="see-also"></a>另请参阅

[非标准行为](../cpp/nonstandard-behavior.md)

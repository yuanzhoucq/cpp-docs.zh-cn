---
title: "内联函数 | Microsoft Docs"
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1583e12613db9d53c0d1fc7be75e21ba377ab940
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="inline-functions"></a>内联函数

**Microsoft 专用**

`__inline` 关键字告诉编译器用函数定义中的代码替换每个函数调用实例。 但是，替换操作完全由编译器自行决定。 例如，如果某个函数的地址被采用或者由于过大而无法内联，则编译器不会内联该函数。

对要作为内联候选项加以考虑的函数，它必须使用新式的函数定义。

请使用以下形式指定内联函数：

> __inline type<sub>opt</sub> function-definition

使用内联函数将生成更快的代码，有时可能生成比等效函数调用所生成的更小的代码，原因如下：

- 它节省了执行函数调用所需的时间。

- 小的内联函数（可能是三行或更少）创建的代码比等效函数调用创建的代码更少，因为编译器不会生成处理参数和返回值的代码。

- 函数生成的内联需要进行普通函数不可用的代码优化，因为编译器不执行过程间优化。

使用 `__inline` 的函数不应与内联汇编常程序代码相混淆。 有关详细信息，请参阅[内联汇编程序](../c-language/inline-assembler-c.md)。

**结束 Microsoft 专用**  

## <a name="see-also"></a>另请参阅

[inline、__inline、\__forceinline](../cpp/inline-functions-cpp.md)


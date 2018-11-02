---
title: 说明符
ms.date: 11/04/2016
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
ms.openlocfilehash: aef967b26321f289cb8c7bd0402d7fe8f12b77b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611401"
---
# <a name="specifiers"></a>说明符

本主题介绍*声明说明符*（声明说明符） 组件[声明](declarations-and-definitions-cpp.md)。

以下占位符和语言关键字为声明说明符：

*存储类说明符*

*类型说明符*

*函数说明符*

[friend](friend-cpp.md)

[typedef](aliases-and-typedefs-cpp.md) `(` *扩展声明修饰符 seq* `)`

[__declspec](declspec.md) `(` *扩展声明修饰符 seq* `)`

## <a name="remarks"></a>备注

*声明说明符*声明的一部分的最长序列是*声明说明符*可以用来表示类型名称，不包括指针或引用修饰符。 声明的其余部分是*声明符*，其中包括引入的名称。

下表列出了四个声明，并随后会列出每个声明*声明说明符*并*声明符*组件分开。

|声明|*声明说明符*|`declarator`|
|-----------------|------------------------|------------------|
|`char *lpszAppName;`|**char**|`*lpszAppName`|
|`typedef char * LPSTR;`|**char**|`*LPSTR`|
|`const int func1();`|**const int**|`func1`|
|`volatile void *pvvObj;`|**易失性 void**|`*pvvObj`|

因为**签名**，**无符号**，**长**，以及**短**都表示**int**、 **typedef**命名为以下任一关键字的成员*声明符列表*不是*声明说明符*。

> [!NOTE]
>  由于可以重新声明名称，因此其解释受当前范围内的最新声明的约束。 重新声明可能会影响如何解释名称的编译器，尤其是**typedef**名称。

## <a name="see-also"></a>请参阅

[声明和定义](declarations-and-definitions-cpp.md)

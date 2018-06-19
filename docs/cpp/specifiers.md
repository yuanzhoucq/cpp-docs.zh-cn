---
title: 说明符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2888f8a75e9b7addd2b8f195ffbf875c2b7ae1a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422321"
---
# <a name="specifiers"></a>说明符
本主题介绍*声明说明符*（声明说明符） 组件[声明](declarations-and-definitions-cpp.md)。  
  
 以下占位符和语言关键字为声明说明符：  
  
 *存储类说明符*  
  
 *类型说明符*  
  
 *函数说明符*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)  
  
 [__declspec](../cpp/declspec.md) `(` *扩展声明修饰符 seq* `)`  
  
## <a name="remarks"></a>备注  
 *声明说明符*声明一部分的最长序列是*声明说明符*可以用来表示类型名称，不包括指针或引用修饰符。 声明的剩余部分*声明符*，其中包括引入的名称。  
  
 下表列出了四个声明，并随后会列出每个声明*声明说明符*和*声明符*组件单独。  
  
|声明|*声明说明符*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|`char`|`*lpszAppName`|  
|`typedef char * LPSTR;`|`char`|`*LPSTR`|  
|`const int func1();`|`const int`|`func1`|  
|`volatile void *pvvObj;`|`volatile void`|`*pvvObj`|  
  
 因为`signed`， `unsigned`， `long`，和`short`都表示`int`、`typedef`命名这些关键字之一将其视为属于以下*声明符列表*不的*声明说明符*。  
  
> [!NOTE]
>  由于可以重新声明名称，因此其解释受当前范围内的最新声明的约束。 重新声明可能影响编译器解释名称的方式，尤其是 `typedef` 名称。  
  
## <a name="see-also"></a>请参阅  
 [声明和定义](declarations-and-definitions-cpp.md)
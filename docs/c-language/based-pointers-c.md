---
title: 基指针 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b414110b0f3367c2b589f82915f417ea7389d738
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="based-pointers-c"></a>基指针 (C)
**Microsoft 专用**  
  
 [__based（C++ 参考）](../cpp/based-pointers-cpp.md)  
  
 对于 Microsoft 32 位和 64 位 C 编译器，基指针是相对于 32 位或 64 位指针基的 32 位或 64 位偏移量。 基寻址对于控制分配对象的部分很有用，这可减少可执行文件的大小并加快执行速度。 通常，用于指定基指针的形式为  
  
```  
  
type  
__based(  
base  
)  
declarator  
  
```  
  
 基寻址的“based on pointer”变体支持作为基的指针的规范。 该基指针是内存部分的偏移量，它从所基于的指针开始。 基于指针地址的指针是 32 位和 64 位编译中唯一有效的 `__based` 关键字形式。 在这些编译中，它们是来自 32 位或 64 位基的 32 位或 64 位置换。  
  
 基于指针的指针的用途之一是用于包含指针的永久标识符。 可将包含基于指针的指针的链接列表保存到磁盘，然后重新加载到内存中的另一个位置，并且指针保持有效。  
  
 以下示例演示基于指针的指针。  
  
```  
void *vpBuffer;  
  
struct llist_t  
{  
    void __based( vpBuffer ) *vpData;  
    struct llist_t __based( vpBuffer ) *llNext;  
};  
```  
  
 将指针 `vpBuffer` 分配给程序中后面某个时间点分配的内存地址。 相对于 `vpBuffer` 的值重新定位链接的列表。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [声明符和变量声明](../c-language/declarators-and-variable-declarations.md)
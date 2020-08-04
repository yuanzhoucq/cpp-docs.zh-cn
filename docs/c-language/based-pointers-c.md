---
title: 基指针 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
ms.openlocfilehash: d1ef1ec98d718e408621f5303e809d09020d5719
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87190242"
---
# <a name="based-pointers-c"></a>基指针 (C)

**Microsoft 专用**

[__based（C++ 参考）](../cpp/based-pointers-cpp.md)

对于 Microsoft 32 位和 64 位 C 编译器，基指针是相对于 32 位或 64 位指针基的 32 位或 64 位偏移量。 基寻址对于控制分配对象的部分很有用，这可减少可执行文件的大小并加快执行速度。 通常，用于指定基指针的形式为

> *type* **__based(** *base* **)** *declarator*

基寻址的“based on pointer”变体支持作为基的指针的规范。 该基指针是内存部分的偏移量，它从所基于的指针开始。 基于指针地址的指针是 `__based` 关键字的唯一有效的 32 位和 64 位编译 形式。 在这些编译中，它们是来自 32 位或 64 位基的 32 位或 64 位置换。

基于指针的指针的用途之一是用于包含指针的永久标识符。 可将包含基于指针的指针的链接列表保存到磁盘，然后重新加载到内存中的另一个位置，并且指针保持有效。

以下示例演示基于指针的指针。

```C
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

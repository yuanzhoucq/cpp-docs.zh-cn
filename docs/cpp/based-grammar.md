---
title: __based 语法
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 539ccef65477bafe2c46ce328bdaf65f52aff1b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229150"
---
# <a name="__based-grammar"></a>__based 语法

**Microsoft 专用**

在需要精确控制将对象分配到的段（基于静态和动态的数据）时，基寻址很有用。

32位和64位编译中唯一可接受的基于寻址的寻址形式是 "基于指针"，它定义一个类型，该类型包含对32或64或或的32位64或基于 **`void`** 。

## <a name="grammar"></a>语法

*基于范围的修饰符*： **__based （**  *基表达式*  **）**

*基表达式*： *variablebased-declaratorsegment-namesegment-强制转换*

*基于变量*：*标识符*

*基于抽象的-声明符*：*抽象声明符*

*基类型*：*类型名称*

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[基指针](../cpp/based-pointers-cpp.md)

---
title: __based 语法
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: a8c923b5a111144c539b5bea1b2f47eb58dd1fbd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857640"
---
# <a name="__based-grammar"></a>__based 语法

**Microsoft 专用**

在需要精确控制将对象分配到的段（基于静态和动态的数据）时，基寻址很有用。

32位和64位编译中唯一可接受的基于寻址形式的寻址是 "基于指针"，它定义一个类型，该类型包含对32位或64或或基于**void**的32位或64位置换。

## <a name="grammar"></a>语法

*based-range-modifier*: **__based(**  *base-expression*  **)**

*基表达式*： *variablebased-declaratorsegment-namesegment-强制转换*

*基于变量*：*标识符*

*基于抽象的-声明符*：*抽象声明符*

*基类型*：*类型名称*

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[基指针](../cpp/based-pointers-cpp.md)
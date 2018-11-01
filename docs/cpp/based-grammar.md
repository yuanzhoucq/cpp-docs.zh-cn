---
title: __based 语法
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 8dec9b0bcc7db25e2ec4c39b9d907922691bfc05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558140"
---
# <a name="based-grammar"></a>__based 语法

## <a name="microsoft-specific"></a>Microsoft 专用

在需要精确控制将对象分配到的段（基于静态和动态的数据）时，基寻址很有用。

基寻址的 32 位和 64 位编译中可接受"基于指针"的唯一形式，它定义一个包含与 32 位或 64 位基的 32 位或 64 位的位移或基于**void**。

## <a name="grammar"></a>语法

*基于范围修饰符*: **__based (***基表达式***)** 

*基础表达式*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*基于变量*:*标识符*

*基于抽象声明符*:*抽象声明符*

*基类型*:*类型名称*

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[基指针](../cpp/based-pointers-cpp.md)
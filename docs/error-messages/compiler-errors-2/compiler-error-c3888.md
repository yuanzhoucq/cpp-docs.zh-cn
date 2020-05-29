---
title: 编译器错误 C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 40156dfaad5965d30a32d3aa2ac574a5f91999ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176399"
---
# <a name="compiler-error-c3888"></a>编译器错误 C3888

“name”：C++/CLI 不支持与此 literal 数据成员关联的常量表达式

使用 *literal* 关键字声明的 [名称](../../extensions/literal-cpp-component-extensions.md) 数据成员是使用编译器不支持的值初始化的。 编译器仅支持常量整型、枚举或字符串类型。 **C3888** 错误可能的原因是数据成员是使用字节数组初始化的。

### <a name="to-correct-this-error"></a>更正此错误

1. 检查声明的 literal 数据成员是否是支持的类型。

## <a name="see-also"></a>请参阅

[名称](../../extensions/literal-cpp-component-extensions.md)

---
title: 编译器错误 C3888 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9292f54fee467a5f8d01202b6ed7ca991b52d43
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096452"
---
# <a name="compiler-error-c3888"></a>编译器错误 C3888

“name”：C++/CLI 不支持与此 literal 数据成员关联的常量表达式

使用 *literal* 关键字声明的 [名称](../../windows/literal-cpp-component-extensions.md) 数据成员是使用编译器不支持的值初始化的。 编译器仅支持常量整型、枚举或字符串类型。 **C3888** 错误可能的原因是数据成员是使用字节数组初始化的。

### <a name="to-correct-this-error"></a>更正此错误

1. 检查声明的 literal 数据成员是否是支持的类型。

## <a name="see-also"></a>请参阅

[名称](../../windows/literal-cpp-component-extensions.md)
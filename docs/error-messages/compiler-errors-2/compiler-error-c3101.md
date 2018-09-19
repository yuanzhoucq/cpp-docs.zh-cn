---
title: 编译器错误 C3101 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3101
dev_langs:
- C++
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69f881206528d83dc298fd262dd54c1dd84a7308
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049827"
---
# <a name="compiler-error-c3101"></a>编译器错误 C3101

命名的特性参数 field 的表达式非法

在初始化命名的特性参数时，值必须是一个编译时常数。

有关属性的详细信息，请参阅[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3101。

```
// C3101.cpp
// compile with: /clr /c
ref class AAttribute : System::Attribute {
public:
   int Field;
};

extern int i;

[assembly:A(Field = i)];   // C3101
[assembly:A(Field = 0)];   // OK
```
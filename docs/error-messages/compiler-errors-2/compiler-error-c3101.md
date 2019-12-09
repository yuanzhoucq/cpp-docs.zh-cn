---
title: 编译器错误 C3101
ms.date: 11/04/2016
f1_keywords:
- C3101
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
ms.openlocfilehash: dca91b9359417b8c4cce9329e2aa25107016c086
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749995"
---
# <a name="compiler-error-c3101"></a>编译器错误 C3101

命名特性参数 "field" 的表达式非法

初始化命名特性参数时，该值必须是编译时常量。

有关特性的详细信息，请参阅[用户定义的属性](../../extensions/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3101。

```cpp
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

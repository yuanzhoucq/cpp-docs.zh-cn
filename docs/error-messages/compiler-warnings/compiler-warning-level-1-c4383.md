---
title: 编译器警告 （等级 1） C4383 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4383
dev_langs:
- C++
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e4ac56b4f94ee6ff7e6ade01dfadca0c00a92db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094840"
---
# <a name="compiler-warning-level-1-c4383"></a>编译器警告（等级 1）C4383

instance_dereference_operator： 取消引用句柄的意义可以更改，用户定义 operator 运算符存在;将该运算符编写为有关操作数的显式静态函数

添加时的取消引用运算符是用户定义的实例的重写的托管类型中，可能会重写的类型的取消引用运算符返回句柄的对象的功能。 请考虑编写一个静态的、 用户定义取消引用运算符。

有关详细信息，请参阅[句柄对象运算符 (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md)并[跟踪引用运算符](../../windows/tracking-reference-operator-cpp-component-extensions.md)。

此外，实例运算符不供其他语言编译器通过引用的元数据。 有关详细信息，请参阅[用户定义的运算符 (C + + CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C4383。

```
// C4383.cpp
// compile with: /clr /W1

ref struct S {
   int operator*() { return 0; }   // C4383
};

ref struct T {
   static int operator*(T%) { return 0; }
};

int main() {
   S s;
   S^ pS = %s;

   T t;
   T^ pT = %t;
   T% rT = *pT;
}
```
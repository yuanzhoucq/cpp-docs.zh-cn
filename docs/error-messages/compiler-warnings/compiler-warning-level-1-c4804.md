---
title: 编译器警告 （等级 1） C4804 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd1d1659ad6c8716cebf37a99f234af7b41f5745
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094801"
---
# <a name="compiler-warning-level-1-c4804"></a>编译器警告（等级 1）C4804

operation： 不安全地使用操作中的 bool 类型

在使用时，此警告是为`bool`变量或以意外方式的值。 例如，如果您使用的运算符，如负一元运算符生成 C4804 (**-**) 或二进制反码运算符 (`~`)。 编译器计算的表达式。

## <a name="example"></a>示例

下面的示例生成 C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```
---
title: 编译器警告 （等级 C4201 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4201
dev_langs:
- C++
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 702ce23333e29548e9bfe092c15ae60c5652168e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096933"
---
# <a name="compiler-warning-level-4-c4201"></a>编译器警告（等级 4）C4201

使用了非标准扩展： 无名称结构/联合

在 Microsoft 扩展 (/Ze) 中，可以指定而无需声明符的结构，为另一个结构或联合的成员。 这些结构生成 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>示例

```
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```
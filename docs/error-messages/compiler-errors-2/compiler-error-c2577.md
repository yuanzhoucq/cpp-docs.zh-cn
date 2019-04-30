---
title: 编译器错误 C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 4406aa90b26bc517308132ae9cccd003d44a9aad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408454"
---
# <a name="compiler-error-c2577"></a>编译器错误 C2577

member： 析构函数/终结器不能有返回类型

析构函数或终结器不能返回值为`void`或任何其他类型。 删除`return`从析构函数定义的语句。

## <a name="example"></a>示例

下面的示例生成 C2577。

```
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
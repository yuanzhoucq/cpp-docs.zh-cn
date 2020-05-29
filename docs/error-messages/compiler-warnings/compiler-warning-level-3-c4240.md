---
title: 编译器警告（等级 3）C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 9e4d33bd0151e4355903c7d10b667ced405a2471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161563"
---
# <a name="compiler-warning-level-3-c4240"></a>编译器警告（等级 3）C4240

使用了非标准扩展：对 "classname" 的访问现在被定义为 "访问说明符"，而以前被定义为 "access 说明符"

在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下，不能更改对嵌套类的访问。 在默认的 Microsoft 扩展（/Ze）下，可以通过此警告。

## <a name="example"></a>示例

```cpp
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```

---
title: 编译器错误 C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 788f03e4364404ad5c30b7edcba8b743c7f201ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152418"
---
# <a name="compiler-error-c3846"></a>编译器错误 C3846

symbol： 无法导入 assembly2 中的符号： 因为 symbol 具有已导入从另一个程序集 assembly1

不是从引用的程序集导入一个符号，因为从引用的程序集以前导入。

## <a name="example"></a>示例

下面的示例生成 C3846:

```
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

然后编译这段：

```
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```

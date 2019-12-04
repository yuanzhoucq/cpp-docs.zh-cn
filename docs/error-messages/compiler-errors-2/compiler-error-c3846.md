---
title: 编译器错误 C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: a4c51ccfc724cf8309044812b287677f0f1a2ff0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754896"
---
# <a name="compiler-error-c3846"></a>编译器错误 C3846

"symbol"：无法从 "assembly2" 导入符号：因为 "symbol" 已从另一个程序集 "assembly1" 导入

无法从引用的程序集导入符号，因为它以前是从引用的程序集导入的。

## <a name="example"></a>示例

下面的示例生成 C3846：

```cpp
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

然后编译以下内容：

```cpp
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```

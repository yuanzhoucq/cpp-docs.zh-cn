---
title: 编译器警告（等级 4）C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: ba2e1e7eb490a28626937a3911608ff9686d6f38
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195975"
---
# <a name="compiler-warning-level-4-c4565"></a>编译器警告（等级 4）C4565

> "*function*"：重定义;符号以前是用 __declspec （*修饰符*）声明的

## <a name="remarks"></a>备注

重定义或重新声明符号，并且第二个定义或声明不同于第一个定义或声明，没有 **`__declspec`** 修饰符（*修饰符*）。 此警告为信息性。 若要修复此警告，请删除其中一个定义。

## <a name="example"></a>示例

下面的示例生成 C4565：

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```

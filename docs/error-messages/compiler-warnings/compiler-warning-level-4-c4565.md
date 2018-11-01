---
title: 编译器警告（等级 4）C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: b655dcfb456d32e45833e89e5a48926ad70d1d9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588677"
---
# <a name="compiler-warning-level-4-c4565"></a>编译器警告（等级 4）C4565

> '*函数*： 重定义; 符号之前声明的使用 __declspec (*修饰符*)

## <a name="remarks"></a>备注

已重新定义或重新声明一个符号和第二个定义或声明中的，不同于第一个定义或声明中，没有`__declspec`修饰符 (*修饰符*)。 此警告为信息性。 若要解决此警告，请删除其中一个定义。

## <a name="example"></a>示例

下面的示例生成 C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
---
title: 编译器警告（等级 4）C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: afb4fb493c7c3e34ca691720a30d74517b0ab5b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220867"
---
# <a name="compiler-warning-level-4-c4559"></a>编译器警告（等级 4）C4559

> '*函数*： 重定义; 函数提升 __declspec (*修饰符*)

## <a name="remarks"></a>备注

函数已重新定义或重新声明并添加第二个定义或声明 **__declspec**修饰符 (*修饰符*)。 此警告为信息性。 若要解决此警告，请删除其中一个定义。

## <a name="example"></a>示例

下面的示例生成 C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
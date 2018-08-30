---
title: 编译器警告 （等级 C4565 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c25f2f1fc16c6d45a7d1eddec8d3efe62db142f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211257"
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
---
title: 编译器警告 （等级 C4559 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5743b33f62aa954c3765b729ab5c0297b20e32
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195571"
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
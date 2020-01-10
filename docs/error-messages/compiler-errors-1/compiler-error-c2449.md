---
title: 编译器错误 C2449
ms.date: 11/04/2016
f1_keywords:
- C2449
helpviewer_keywords:
- C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
ms.openlocfilehash: 6fd62813fdf3b50c0e329fc423e100d55a36ae12
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299018"
---
# <a name="compiler-error-c2449"></a>编译器错误 C2449

在文件范围内找到 "{" （是否缺少函数头？）

在文件范围内出现左大括号。

此错误可能是由函数头与函数定义的左大括号之间的分号引起的。

下面的示例生成 C2499：

```c
// C2449.c
// compile with: /c
void __stdcall func(void) {}   // OK
void __stdcall func(void);  // extra semicolon on this line
{                         // C2449 detected here
```

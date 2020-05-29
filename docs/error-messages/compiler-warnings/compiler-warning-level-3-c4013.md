---
title: 编译器警告（等级3） C4013
ms.date: 11/04/2016
f1_keywords:
- C4013
helpviewer_keywords:
- C4013
ms.assetid: 9f9afc71-6e78-463d-9d66-3012d6a3cd5d
ms.openlocfilehash: 7aa35b7ebf918bfdc6413df17582ebb747058e52
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161706"
---
# <a name="compiler-warning-level-3-c4013"></a>编译器警告（等级3） C4013

未定义 "function";假定 extern 返回 int

编译器遇到了对未定义的函数的调用。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 函数名称的拼写不正确

1. 外部函数未原型为 `extern`

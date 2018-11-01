---
title: 编译器错误 C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: f6e33d0e0ee139138df7d8e11357100b3ec3a1a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593435"
---
# <a name="compiler-error-c2818"></a>编译器错误 C2818

重载“operator ->”的应用程序通过类型“type”进行递归

类成员访问运算符重新定义包含递归`return`语句。 若要重新定义`->`递归运算符，必须移动到单独的函数调用运算符从的递归例程来重写函数。
---
title: 编译器错误 C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 786a38aca2c3b9674969018d9e5766eed29c358c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212665"
---
# <a name="compiler-error-c2818"></a>编译器错误 C2818

重载 "operator->" 的应用程序是通过类型 "type" 递归的

类成员访问运算符的重定义包含递归 **`return`** 语句。 若要 `->` 使用递归重新定义运算符，必须将递归例程移到从运算符 override 函数调用的单独函数。

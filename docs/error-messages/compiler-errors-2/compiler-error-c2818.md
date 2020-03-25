---
title: 编译器错误 C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 00952e55f1b732bd9af3733f5c0ec575a39116fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202100"
---
# <a name="compiler-error-c2818"></a>编译器错误 C2818

重载 "operator->" 的应用程序是通过类型 "type" 递归的

类成员访问运算符的重定义包含递归 `return` 语句。 若要使用递归重定义 `->` 运算符，必须将递归例程移到从运算符 override 函数调用的单独函数。

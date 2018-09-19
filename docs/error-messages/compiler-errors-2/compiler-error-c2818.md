---
title: 编译器错误 C2818 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2818
dev_langs:
- C++
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f692f52477c988c277f60a689dac5ce83a90acb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112039"
---
# <a name="compiler-error-c2818"></a>编译器错误 C2818

重载“operator ->”的应用程序通过类型“type”进行递归

类成员访问运算符重新定义包含递归`return`语句。 若要重新定义`->`递归运算符，必须移动到单独的函数调用运算符从的递归例程来重写函数。
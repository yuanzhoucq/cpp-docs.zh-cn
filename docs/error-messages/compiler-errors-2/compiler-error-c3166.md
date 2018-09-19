---
title: 编译器错误 C3166 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3166
dev_langs:
- C++
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c568f1732a4be5d890a5a654b09638828385383
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035508"
---
# <a name="compiler-error-c3166"></a>编译器错误 C3166

指针： 不能将指向内部 __gc 指针的指针声明为 type 的成员

编译器找到了无效的指针声明 (`__nogc`指针，指向`__gc`指针。)。

C3166 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。

---
title: 编译器错误 C2696 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6e76b0c11d329c734b0609c540aca4315c7ed9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108737"
---
# <a name="compiler-error-c2696"></a>编译器错误 C2696

无法创建临时对象的托管类型 type

对引用`const`非托管程序中会导致编译器调用构造函数，并在堆栈上创建临时对象。 但是，永远不会可以在堆栈上创建托管的类。

C2696 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。

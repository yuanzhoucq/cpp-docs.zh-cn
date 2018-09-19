---
title: 编译器错误 C2873 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2873
dev_langs:
- C++
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf0cc5663d81d6c1e7ad6a9f1a5f7ca167f12909
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049899"
---
# <a name="compiler-error-c2873"></a>编译器错误 C2873

symbol： 不能在使用声明中使用符号

一个`using`缺少指令[命名空间](../../cpp/namespaces-cpp.md)关键字。 这将导致编译器错误地解释为代码[using 声明](../../cpp/using-declaration.md)而非[using 指令](../../cpp/namespaces-cpp.md#using_directives)。
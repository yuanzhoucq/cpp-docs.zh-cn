---
title: 错误 C1055 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6960d8168bd818e4d1baa30e5e54940e6e4dc2e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115445"
---
# <a name="fatal-error-c1055"></a>错误 C1055

编译器限制： 超出键

源代码文件包含的符号太多。 编译器用尽了符号表的哈希键。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 将源文件拆分为较小的文件。

1. 消除不必要的标头文件。

1. 重复使用而不是创建新的临时和全局变量。
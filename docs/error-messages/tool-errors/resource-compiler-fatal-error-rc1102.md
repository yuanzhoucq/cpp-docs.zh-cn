---
title: 资源编译器错误 RC1102 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1102
dev_langs:
- C++
helpviewer_keywords:
- RC1102
ms.assetid: bd2091f8-ef5e-4151-a8d6-98043e9422b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2be0a62b08b361f1cfa423fa3999a440e2fe4709
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073172"
---
# <a name="resource-compiler-fatal-error-rc1102"></a>资源编译器错误 RC1102

内部错误： RCPP 参数太多

对资源编译器预处理器传递的参数太多。 减少使用定义的符号定义的符号的数量 (/d) 在您的源中定义它们的选项。 此外可以通过指定过许多包含文件搜索路径使用包含搜索路径选项导致此错误 (/ 我)。
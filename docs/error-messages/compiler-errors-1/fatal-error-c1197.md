---
title: 错误 C1197 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1197
dev_langs:
- C++
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58561e7bd906fc750779ef53a4f68ec27088a3b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024757"
---
# <a name="fatal-error-c1197"></a>错误 C1197

不能引用 mscorlib.dll_1，因为程序已经引用 mscorlib.dll_2

编译器与公共语言运行时版本匹配。  但是，尝试从以前的版本中引用公共语言运行时文件的版本。

若要解决此错误，只能从与正在使用编译的 Visual c + + 版本附带的公共语言运行时版本引用文件。

## <a name="example"></a>示例

下面的示例生成 C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
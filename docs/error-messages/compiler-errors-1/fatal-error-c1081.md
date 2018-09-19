---
title: 错误 C1081 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b34f2f19a0bb8770ea9292fef120c415c0fb255a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060521"
---
# <a name="fatal-error-c1081"></a>错误 C1081

symbol： 文件名太长

文件路径名的长度超过了`_MAX_PATH`（由 stdlib.h 定义为 260 个字符）。 缩短的文件的名称。

如果使用包含短文件名调用 CL.exe，编译器可能需要生成完整的路径名。 例如，`cl -c myfile.cpp`可能会导致编译器生成：

```
D:\<very-long-directory-path>\myfile.cpp
```
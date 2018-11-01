---
title: 错误 C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: f3c9f9bde5da7fb120accbb9a8d72e5715ab9d2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569663"
---
# <a name="fatal-error-c1081"></a>错误 C1081

symbol： 文件名太长

文件路径名的长度超过了`_MAX_PATH`（由 stdlib.h 定义为 260 个字符）。 缩短的文件的名称。

如果使用包含短文件名调用 CL.exe，编译器可能需要生成完整的路径名。 例如，`cl -c myfile.cpp`可能会导致编译器生成：

```
D:\<very-long-directory-path>\myfile.cpp
```
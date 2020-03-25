---
title: 错误 C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: b8630a26d14c68a5f1abe45bb0b8d0141d0dedbb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204186"
---
# <a name="fatal-error-c1081"></a>错误 C1081

"symbol"：文件名太长

文件路径名的长度超过 `_MAX_PATH` （由 STDLIB.H 定义为260个字符）。 缩短文件的名称。

如果调用带短文件名的 CL，则编译器可能需要生成完整路径名。 例如，`cl -c myfile.cpp` 可能导致编译器生成：

```
D:\<very-long-directory-path>\myfile.cpp
```

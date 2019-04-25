---
title: 错误 C1104
ms.date: 11/04/2016
f1_keywords:
- C1104
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
ms.openlocfilehash: c10d1a89d854aaeac47a9a70f1e1e319d1662935
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174230"
---
# <a name="fatal-error-c1104"></a>错误 C1104

导入 libid 时遇到错误：“message”

导入类型库时编译器检测到问题。  例如，你不能使用 libid 指定类型库，同时还指定 `no_registry`。

有关详细信息，请参阅[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。

下面的示例生成 C1104：

```
// C1104.cpp
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104
```
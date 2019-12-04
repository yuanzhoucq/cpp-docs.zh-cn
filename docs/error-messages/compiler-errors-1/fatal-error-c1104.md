---
title: 错误 C1104
ms.date: 11/04/2016
f1_keywords:
- C1104
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
ms.openlocfilehash: a26e65e98b44a69eb14daf6d835fafb23362dfa2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747327"
---
# <a name="fatal-error-c1104"></a>错误 C1104

导入 libid 时遇到错误：“message”

导入类型库时编译器检测到问题。  例如，你不能使用 libid 指定类型库，同时还指定 `no_registry`。

有关详细信息，请参阅[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。

下面的示例生成 C1104：

```cpp
// C1104.cpp
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104
```

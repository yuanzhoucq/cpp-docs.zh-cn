---
title: 错误 C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: f037d1acb281b5997e3486a542784abc4b4b7542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747379"
---
# <a name="fatal-error-c1103"></a>错误 C1103

导入 progid 时遇到错误：“message”

导入类型库时编译器检测到问题。  例如，你不能使用 progid 指定类型库，同时还指定 `no_registry`。

有关详细信息，请参阅[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。

下面的示例生成 C1103：

```cpp
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```

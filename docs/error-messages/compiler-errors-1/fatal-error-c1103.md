---
title: 错误 C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: b6253af9fcf400321fb58d4d8a6d7aacf461b926
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174193"
---
# <a name="fatal-error-c1103"></a>错误 C1103

导入 progid 时遇到错误：“message”

导入类型库时编译器检测到问题。  例如，你不能使用 progid 指定类型库，同时还指定 `no_registry`。

有关详细信息，请参阅[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。

下面的示例生成 C1103：

```
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```
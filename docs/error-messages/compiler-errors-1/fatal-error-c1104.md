---
title: 错误 C1104 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1104
dev_langs:
- C++
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e624238a1b7616ab84a655839a05cfd6899d38ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048105"
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
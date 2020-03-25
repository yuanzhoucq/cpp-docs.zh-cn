---
title: 编译器错误 C3457
ms.date: 11/04/2016
f1_keywords:
- C3457
helpviewer_keywords:
- C3457
ms.assetid: 5c1e366a-fa75-4cca-b9a3-86d4ebe4090e
ms.openlocfilehash: 1481bd1d430aff74bff8140941b0ab218acbe364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200874"
---
# <a name="compiler-error-c3457"></a>编译器错误 C3457

“attribute”：特性不支持未命名参数

源 annotation 特性与 CLR 自定义特性或编译器特性不同，仅支持命名参数。

## <a name="example"></a>示例

以下示例生成 C3457。

```
#include "SourceAnnotations.h"
[vc_attributes::Post( 1 )] int f();   // C3457
[vc_attributes::Post( Valid=vc_attributes::Yes )] int f2();   // OK
```

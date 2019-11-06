---
title: 编译器警告（等级1） C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 456e7d393eb751e99c1969619ccfdcc649193c75
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627054"
---
# <a name="compiler-warning-level-1-c4103"></a>编译器警告（等级1） C4103

"filename"：包含标头后更改了对齐方式，可能是由于缺少 #pragma pack （pop）

打包影响类的布局，并且通常情况下，如果在标头文件中进行封装更改，则可能会出现问题。

在退出标头文件之前，请使用 #pragma [pack](../../preprocessor/pack.md)（pop）来解决此警告。

下面的示例生成 C4103：

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

然后，

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```
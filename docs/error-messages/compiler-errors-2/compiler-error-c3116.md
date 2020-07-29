---
title: 编译器错误 C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: b336588d732fca2fd45b753429a563360f575912
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223442"
---
# <a name="compiler-error-c3116"></a>编译器错误 C3116

"存储说明符"：接口方法的存储类无效

你使用 **`typedef`** **`register`** 了、或 **`static`** 作为接口方法的存储类。 这些存储类在接口成员上不允许。

下面的示例生成 C3116：

```cpp
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```

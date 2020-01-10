---
title: 编译器错误 C2191
ms.date: 11/04/2016
f1_keywords:
- C2191
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
ms.openlocfilehash: 66b7d70b9010855ada7b9d24fba80915450a685b
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301868"
---
# <a name="compiler-error-c2191"></a>编译器错误 C2191

第二个参数列表比第一个长

第二次用更长的参数列表声明了 C 函数。 C 不支持重载函数。

## <a name="example"></a>示例

下面的示例生成 C2191：

```c
// C2191.c
// compile with: /Za /c
void func( int );
void func( int, float );   // C2191 different parameter list
void func2( int, float );   // OK
```

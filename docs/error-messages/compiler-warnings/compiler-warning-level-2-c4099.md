---
title: 编译器警告 （等级 2） C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 09ea9e2963735c1e011e25b42b04ad6d67d084a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471716"
---
# <a name="compiler-warning-level-2-c4099"></a>编译器警告 （等级 2） C4099

identifier： 类型名称以前使用 objecttype1 现在使用 objecttype2

对象声明为结构定义为一个类，或声明为类的对象定义为结构。 编译器将使用定义中提供的类型。

## <a name="example"></a>示例

下面的示例生成 C4099。

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```
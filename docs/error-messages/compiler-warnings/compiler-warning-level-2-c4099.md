---
title: 编译器警告（等级2） C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 97ead14dc9771dc02ad722843ec9fe1a8056e3f6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174279"
---
# <a name="compiler-warning-level-2-c4099"></a>编译器警告（等级2） C4099

"identifier"：首次使用 "objecttype1" 查看的类型名称，现在使用 "objecttype2"

声明为结构的对象被定义为类，或者声明为类的对象定义为结构。 编译器使用定义中给定的类型。

## <a name="example"></a>示例

下面的示例生成 C4099。

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```

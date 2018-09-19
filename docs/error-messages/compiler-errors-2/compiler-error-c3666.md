---
title: 编译器错误 C3666 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3666
dev_langs:
- C++
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8637caadbe439b2da3b64593655ddd75177f353b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084076"
---
# <a name="compiler-error-c3666"></a>编译器错误 C3666

constructor： 重写说明符 keyword 不允许在构造函数

重写说明符用上一个构造函数，并且不允许的。 有关详细信息，请参阅[重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3666。

```
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```
---
title: 编译器错误 C3118
ms.date: 11/04/2016
f1_keywords:
- C3118
helpviewer_keywords:
- C3118
ms.assetid: 40fbe681-8868-4cb2-a2b2-4db4449319a7
ms.openlocfilehash: 072bb821a9dc2547c9a2758fb1ca542bdbc66f86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427399"
---
# <a name="compiler-error-c3118"></a>编译器错误 C3118

interface： 接口不支持虚拟继承

你试图几乎从接口继承。 例如，应用于对象的

```
// C3118.cpp
__interface I1 {
};

__interface I2 : virtual I1 {   // C3118
};
```

生成此错误。
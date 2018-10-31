---
title: 编译器错误 C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: 25798e793bec7d09ea1f307ec1e2d9a63b9dbe27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428101"
---
# <a name="compiler-error-c2978"></a>编译器错误 C2978

语法错误：应为“keyword1”或“keyword2”；却发现类型“keyword3”；泛型中不支持非类型参数

未正确声明泛型类。 请参阅[泛型](../../windows/generics-cpp-component-extensions.md)有关详细信息。

## <a name="example"></a>示例

以下示例生成 C2978：

```
// C2978.cpp
// compile with: /clr /c
generic <ref class T>   // C2978
// try the following line instead
// generic <typename T>   // OK
ref class Utils {
   static void sort(T elems, size_t size);
};

generic <int>
// try the following line instead
// generic <class T>
ref class Utils2 {
   static void sort(T elems, size_t size);
};
```
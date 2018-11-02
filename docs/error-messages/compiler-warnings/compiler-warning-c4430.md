---
title: 编译器警告 C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: 1d58efd57433a065f08e4111302f358405e3b9ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639863"
---
# <a name="compiler-warning-c4430"></a>编译器警告 C4430

缺少类型说明符 - 假定为 int。 注意： c + + 不支持默认 int

为 Visual c + + 2005年执行的编译器一致性工作可以生成此错误： 所有声明必须显式都指定类型;不再被假定为 int。

C4430 始终作为错误发出。  您可以关闭此警告，其中包含`#pragma warning`或 **/wd**; 请参阅[警告](../../preprocessor/warning.md)或[/w、 /W0、 /W1、 /W2、 /W3、 / w4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd、 / /we、 /wo、 /Wv、 /WX （警告级别）](../../build/reference/compiler-option-warning-level.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C4430。

```
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```
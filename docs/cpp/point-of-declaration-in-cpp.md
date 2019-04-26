---
title: C++ 中的声明点
ms.date: 11/04/2016
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
ms.openlocfilehash: d6cb4c3813d88c8b29fbcb2e0827805f406e6c81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183396"
---
# <a name="point-of-declaration-in-c"></a>C++ 中的声明点

名称被视为在紧靠其声明符之后，但位于其（可选）初始值设定项之前的位置进行声明。 (有关声明符的详细信息，请参阅[声明和定义](declarations-and-definitions-cpp.md)。)

请看以下示例：

```cpp
// point_of_declaration1.cpp
// compile with: /W1
double dVar = 7.0;
int main()
{
   double dVar = dVar;   // C4700
}
```

如果声明的 point*后*初始化，然后再在本地`dVar`将初始化为 7.0、 全局变量的值`dVar`。 但是，由于情况并非如此，`dVar` 将初始化为未定义值。

## <a name="see-also"></a>请参阅

[范围](../cpp/scope-visual-cpp.md)
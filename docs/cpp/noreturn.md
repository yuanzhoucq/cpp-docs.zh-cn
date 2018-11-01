---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: 1d78e8f5116eabf9073205b938156197bf1001a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611856"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Microsoft 专用

这 **__declspec**特性告知编译器函数不返回。 因此，编译器了解到调用的代码 **__declspec （noreturn)** 函数不可访问。

如果编译器找到带有不返回值的控制路径的函数，则它会生成警告 (C4715) 或错误消息 (C2202)。 如果由于永远不会返回的函数无法获得的控制路径，则可以使用 **__declspec （noreturn)** 以防止此警告或错误。

> [!NOTE]
>  添加 **__declspec （noreturn)** 到应返回一个函数可能会导致未定义的行为。

## <a name="example"></a>示例

在以下示例中，**其他**子句不包含 return 语句。  声明`fatal`作为 **__declspec （noreturn)** 可避免错误或警告消息。

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)
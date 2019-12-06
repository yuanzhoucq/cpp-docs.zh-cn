---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f9ca61c9d734ccdd6b8d8374ed3a7c4128ee3d5e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857367"
---
# <a name="noreturn"></a>noreturn

**Microsoft 专用**

此 **__declspec**特性告知编译器函数不返回。 因此，编译器知道调用 **__declspec （noreturn）** 函数后的代码是无法访问的。

如果编译器找到带有不返回值的控制路径的函数，则它会生成警告 (C4715) 或错误消息 (C2202)。 如果由于从不返回的函数而无法访问控件路径，则可以使用 **__declspec （noreturn）** 来防止此警告或错误。

> [!NOTE]
>  将 **__declspec （noreturn）** 添加到预期返回的函数可能会导致未定义的行为。

## <a name="example"></a>示例

在下面的示例中， **else**子句不包含 return 语句。  将 `fatal` 声明为 **__declspec （noreturn）** 可避免出现错误或警告消息。

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

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)
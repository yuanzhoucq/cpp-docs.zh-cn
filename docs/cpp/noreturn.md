---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: a30840aa0556a7324ba24c0f2aaec57dea88d082
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367857"
---
# <a name="noreturn"></a>noreturn

**微软特定**

此 **__declspec**属性告诉编译器函数不返回。 因此，编译器知道调用 **__declspec（返回）** 函数后的代码是无法访问的。

如果编译器找到带有不返回值的控制路径的函数，则它会生成警告 (C4715) 或错误消息 (C2202)。 如果由于函数永远不会返回而无法访问控制路径，则可以使用 **__declspec（不返回）** 来防止此警告或错误。

> [!NOTE]
> 向预期返回的函数添加 **__declspec（不返回）** 可能会导致未定义的行为。

## <a name="example"></a>示例

在下面的示例中，**其他**子句不包含返回语句。  声明`fatal`为 **__declspec（不返回）** 可避免错误或警告消息。

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

**结束微软特定**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[Keywords](../cpp/keywords-cpp.md)

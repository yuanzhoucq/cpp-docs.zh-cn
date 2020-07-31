---
title: 编译器错误 C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 0463f6de51e324bd02c8b766fd39909ee2803ecd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212574"
---
# <a name="compiler-error-c3482"></a>编译器错误 C3482

“this”只能在非静态成员函数中用作 lambda 捕获

不能将传递 **`this`** 给在静态方法或全局函数中声明的 lambda 表达式的捕获列表。

### <a name="to-correct-this-error"></a>更正此错误

- 将封闭函数转换为非静态方法，或

- **`this`** 从 lambda 表达式的捕获列表中删除指针。

## <a name="example"></a>示例

以下示例生成 C3482：

```cpp
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>另请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)

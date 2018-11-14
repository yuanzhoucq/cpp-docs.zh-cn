---
title: 编译器错误 C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: 99b2c86d1e914c9425c2664d4e858bba6cb99486
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325548"
---
# <a name="compiler-error-c2842"></a>编译器错误 C2842

> '*类*： 托管或 WinRT 类型不能定义自己的 operator new 或 operator delete

## <a name="remarks"></a>备注

可以定义自己**运算符 new**或**运算符 delete**来管理本机堆上的内存分配。 但是，引用类不能定义这些运算符，因为它们仅分配在托管堆上。

有关详细信息，请参阅[用户定义的运算符 (C + + CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。

## <a name="example"></a>示例

以下示例生成 C2842。

```cpp
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```

---
title: 编译器警告（等级 1）C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 79c8809b4de9d6853aaacec4283bf01d0e89305e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187097"
---
# <a name="compiler-warning-level-1-c4364"></a>编译器警告（等级 1）C4364

\#使用的程序集 "file" 以前在位置（line_number）上出现，无 as_friend 特性;as_friend 未应用

为给定的元数据文件重复了 `#using` 指令，但在第一次出现时未使用 `as_friend` 限定符;编译器将忽略第二个 `as_friend`。

有关详细信息，请参阅[友元C++程序集（）](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>示例

下面的示例创建一个组件。

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>示例

下面的示例生成 C4364。

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```

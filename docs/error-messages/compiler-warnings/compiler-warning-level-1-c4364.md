---
title: 编译器警告（等级 1）C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: db2774b6a73a989b4e9250719f99122826b486fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207103"
---
# <a name="compiler-warning-level-1-c4364"></a>编译器警告（等级 1）C4364

\#使用适用于程序集 file 以前看到没有 as_friend 特性; location(line_number) 在未应用 as_friend

一个`#using`指令重复对于给定的元数据文件，但`as_friend`第一个匹配项中未使用过限定符; 编译器将忽略第二个`as_friend`。

有关详细信息，请参阅[友元程序集 (C++)](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>示例

下面的示例创建一个组件。

```
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>示例

下面的示例生成 C4364。

```
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
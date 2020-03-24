---
title: 编译器警告（等级 1）C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 8a723b7ce7fc79fb6be9c9dd2b500631098622b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163214"
---
# <a name="compiler-warning-level-1-c4251"></a>编译器警告（等级 1）C4251

"identifier"：类 "type" 需要由类 "type2" 的客户端使用的 dll 接口

若要最大程度地减少在使用[__declspec （dllexport）](../../cpp/dllexport-dllimport.md)导出类时数据损坏的可能性，请确保：

- 所有静态数据都可以通过从 DLL 导出的函数进行访问。

- 类的任何内联方法都不能修改静态数据。

- 类的任何内联方法均不使用 CRT 函数或其他库函数使用静态数据（有关详细信息，请参阅[跨 DLL 边界传递 CRT 对象时出现的潜在错误](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)）。

- 类的任何方法（无论内联如何）都可以使用 EXE 和 DLL 中的实例化具有静态数据差异的类型。

可以通过定义用于定义具有虚函数的类的 DLL，以及可以调用来实例化和删除类型的对象的函数，来避免导出类。  然后，就可以对类型调用虚函数。

如果是从C++标准库中的类型派生，编译调试版本（ **/MTd**），并且编译器错误消息引用 _Container_base，则可以忽略 C4251。

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```

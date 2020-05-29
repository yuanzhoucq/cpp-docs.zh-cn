---
title: 编译器警告（等级 1）C4251
ms.date: 04/21/2020
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: 9f261d3deb7f1cac8cd5c60b920e0be49bc8b7a6
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032325"
---
# <a name="compiler-warning-level-1-c4251"></a>编译器警告（等级 1）C4251

> '*类型*' ： 类 '*类型 1*' 需要有 dll 接口，以便类 '类型*2'* 的客户端使用 dll 接口

## <a name="remarks"></a>备注

为了在导出声明为[__declspec（dllexport）](../../cpp/dllexport-dllimport.md)的类时，将数据损坏的可能性降至最低，请确保：

- 所有静态数据都通过从 DLL 导出的函数进行访问。

- 类的内联方法无法修改静态数据。

- 类中联方法不使用 CRT 函数或使用静态数据的其他库函数。 有关详细信息，请参阅通过[DLL 边界传递 CRT 对象的潜在错误](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)。

- 类（无论是否内联）的函数中任何方法都无法使用 EXE 和 DLL 中的实例化具有静态数据差异的类型。

在从 DLL 导出类时，可以避免问题：将类定义为具有虚拟函数，以及实例化和删除类型对象的函数。 然后，您可以调用类型的虚拟函数。

如果类派生自标准库中C++类型，编译调试版本 **（/MTd），** 以及编译器错误消息引用`_Container_base`的位置，则可以忽略 C4251。

## <a name="example"></a>示例

此示例导出派生自`VecWrapper``std::vector`的专用类。

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllexport) VecWrapper : vector<Node *> {};   // C4251
```

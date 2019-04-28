---
title: 编译器警告（等级 2）C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 6e0e80d465d77bd4fe99fbcaa98e289b8a4c8b63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349680"
---
# <a name="compiler-warning-level-2-c4275"></a>编译器警告（等级 2）C4275

> 非 DLL 接口类*class_1*用作基 DLL 接口类*class_2*

将导出的类被派生自不导出的类。

若要导出具有的类时，数据损坏的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，请确保：

- 通过从 DLL 导出的函数访问所有静态数据。

- 您的类没有内联的方法可以修改静态数据。

- 您的类没有内联的方法使用的 CRT 函数或使用静态数据的其他库函数。

- 没有内联的类函数使用的 CRT 函数或其他库函数访问静态数据的位置。

- 您的类没有方法 (而不考虑内联) 可以使用类型其中 EXE 和 DLL 中的实例化具有静态数据的差异。

您可以避免通过定义一个 DLL，它定义了具有虚函数的类和函数，可以调用来实例化并删除对象类型的导出类。  然后，可以只需调用虚函数的类型。

C4275 可以忽略视觉对象中C++如果派生的类型C++标准库，编译调试版本 (**/MTd**)，其中编译器错误消息是指`_Container_base`。

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
---
title: 编译器警告 （等级 2） C4275 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55b93d1ebd81850982b4f6ceac1ceb008ed1fa49
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890278"
---
# <a name="compiler-warning-level-2-c4275"></a>编译器警告（等级 2）C4275

非 DLL 接口 classkey identifier 用作基 DLL 接口 classkey identifier

将导出的类被派生的类中，未导出。

若要导出具有的类时，数据损坏的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，，请确保：

- 通过从 DLL 导出的函数访问所有静态数据。

- 您的类没有内联的方法可以修改静态数据。

- 您的类没有内联的方法使用的 CRT 函数或其他库函数使用静态数据。

- 没有内联的类函数使用的 CRT 函数或其他库函数，其中，例如，访问静态数据。

- 您的类没有方法 (而不考虑内联) 可以使用类型其中 EXE 和 DLL 中的实例化具有静态数据的差异。

您可以避免通过定义一个 DLL，它定义了具有虚函数的类和函数，可以调用来实例化并删除对象类型的导出类。  然后，可以只需调用虚函数的类型。

如果从 c + + 标准库，编译调试版本中的类型派生，可以在 Visual c + + 中忽略 C4275 (**/MTd**)，其中编译器错误消息是指 _Container_base。

```
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```
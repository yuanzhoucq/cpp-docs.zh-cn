---
title: dllexport、dllimport
ms.date: 11/04/2016
f1_keywords:
- dllimport_cpp
- dllexport_cpp
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
ms.openlocfilehash: 0a8d90770552b8b9ab9169378289108d91811216
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189450"
---
# <a name="dllexport-dllimport"></a>dllexport、dllimport

**Microsoft 专用**

**Dllexport**和**dllimport**存储类特性是特定于 Microsoft 的 C C++语言扩展。 可以使用它们从 DLL 中导出或向其中导入函数、数据和对象。

## <a name="syntax"></a>语法

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>备注

这些特性显式定义 DLL 到其客户端的接口，可以是可执行文件或另一个 DLL。 将函数声明为**dllexport**可消除对模块定义（.def）文件的需要，至少与导出函数的规范有关。 **Dllexport**属性替换 **__export**关键字。

如果将类标记为 declspec(dllexport)，则类层次结构中类模板的任何专用化都将隐式标记为 declspec(dllexport)。 这意味着类模板将进行显式实例化，且必须定义类的成员。

函数的**dllexport**使用其修饰名称公开函数。 对于 C++ 函数，这包括名称重整。 对于 C 函数或声明为 `extern "C"` 的函数，这包括基于调用约定的平台特定修饰。 有关 C/C++代码中的名称修饰的信息，请参阅[修饰名](../build/reference/decorated-names.md)。 名称修饰不适用于导出的 C 函数或使用 `extern "C"` 调用约定的 C++ `__cdecl` 函数。

若要导出未修饰名，可以通过使用模块定义 (.def) 文件进行链接，该文件在 EXPORTS 部分定义未修饰名。 有关详细信息，请参阅[导出](../build/reference/exports.md)。 导出未修饰名称的另一种方法是在源代码中使用 `#pragma comment(linker, "/export:alias=decorated_name")` 指令。

声明**dllexport**或**dllimport**时，必须使用扩展的[特性语法](../cpp/declspec.md)和 **__declspec**关键字。

## <a name="example"></a>示例

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

或者，若要提高代码的可读性，可以使用宏定义：

```cpp
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllImport int j;
DllExport int n;
```

有关详细信息，请参阅：

- [定义和声明](../cpp/definitions-and-declarations-cpp.md)

- [使用 dllexport 和 dllimport 定义内联 (C++) 函数](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [一般规则和限制](../cpp/general-rules-and-limitations.md)

- [在 C++ 类中使用 dllimport 和 dllexport](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)

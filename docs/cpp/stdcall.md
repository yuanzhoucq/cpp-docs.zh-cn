---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: 3abd1d020e4181a42a7bc38319e5e17e69ef0507
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178532"
---
# <a name="__stdcall"></a>__stdcall

**__Stdcall**调用约定用于调用 Win32 API 函数。 被调用方清理堆栈，因此编译器将 `vararg` 函数 **__cdecl**。 使用此调用约定的函数需要一个函数原型。 **__Stdcall**修饰符是 Microsoft 特定的。

## <a name="syntax"></a>语法

> *返回类型* **\_\_stdcall** *[* **（** *参数列表* **）** ]

## <a name="remarks"></a>备注

以下列表显示此调用约定的实现。

|元素|实现|
|-------------|--------------------|
|参数传递顺序|从右到左。|
|参数传递约定|按值，除非传递指针或引用类型。|
|堆栈维护职责|调用的函数从堆栈中弹出自己的参数。|
|名称修饰约定|下划线 (_) 是名称的前缀。 名称后跟后面是自变量列表中的字节数（采用十进制）的符号 (@)。 因此，声明为 `int func( int a, double b )` 的函数按如下所示进行修饰：`_func@12`|
|大小写转换约定|无|

[/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md)编译器选项为未使用不同调用约定显式声明的所有函数指定 **__stdcall** 。

为了与早期版本兼容， **_stdcall**是 **__stdcall**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

使用 **__stdcall**修饰符声明的函数以与使用[__cdecl](../cpp/cdecl.md)声明的函数相同的方式返回值。

在 ARM 和 x64 处理器上，编译器接受并忽略 **__stdcall** ;在 ARM 和 x64 体系结构上，按照约定，参数将在寄存器中传递（如果可能），并且后续参数将在堆栈上传递。

对于非静态类函数，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。 也就是说，对于类非静态成员方法，在定义时假定声明期间指定的调用约定。 给定此类定义，

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

此

```cpp
void CMyClass::mymethod() { return; }
```

等效于此

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>示例

在下面的示例中，使用 **__stdcall**会导致所有 `WINAPI` 函数类型作为标准调用进行处理：

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>另请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)<br/>
[关键字](../cpp/keywords-cpp.md)

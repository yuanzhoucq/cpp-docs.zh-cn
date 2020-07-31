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
ms.openlocfilehash: 85d1b29fddece741aa94364bb6edfdf3b973faaf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213172"
---
# <a name="__stdcall"></a>__stdcall

**`__stdcall`** 调用约定用于调用 Win32 API 函数。 被调用方清理堆栈，因此编译器将生成 `vararg` 函数 **`__cdecl`** 。 使用此调用约定的函数需要一个函数原型。 **`__stdcall`** 修饰符是 Microsoft 特定的。

## <a name="syntax"></a>语法

> *返回类型* **`__stdcall`***函数名称*[ **`(`** *参数列表* **`)`** ]

## <a name="remarks"></a>备注

以下列表显示此调用约定的实现。

|元素|实施|
|-------------|--------------------|
|参数传递顺序|从右到左。|
|参数传递约定|按值，除非传递指针或引用类型。|
|堆栈维护职责|调用的函数从堆栈中弹出自己的参数。|
|名称修饰约定|下划线（ `_` ）是名称的前缀。 该名称后跟 "in" 符号（ `@` ），后跟自变量列表中的字节数（以十进制为单位）。 因此，声明为 `int func( int a, double b )` 的函数按如下所示进行修饰：`_func@12`|
|大小写转换约定|无|

[/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md)编译器选项 **`__stdcall`** 为所有未使用不同调用约定显式声明的函数指定。

对于与以前版本的兼容性，为， **`_stdcall`** **`__stdcall`** 除非指定编译器选项 " [ `/Za` \( 禁用语言扩展](../build/reference/za-ze-disable-language-extensions.md)"，否则将是同义词。

使用 **`__stdcall`** 修饰符声明的函数以与使用声明的函数相同的方式返回值 [`__cdecl`](../cpp/cdecl.md) 。

在 ARM 和 x64 处理器上，由 **`__stdcall`** 编译器接受和忽略; 在 ARM 和 x64 体系结构上，按照约定，参数在寄存器中传递（如果可能），后面的参数在堆栈上传递。

对于非静态类函数，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。 也就是说，对于类非静态成员方法，在定义时假定声明期间指定的调用约定。 给定此类定义，

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

等效于此

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>示例

在下面的示例中，在 **`__stdcall`** `WINAPI` 作为标准调用处理的所有函数类型中使用结果：

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>另请参阅

[参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)<br/>
[关键字](../cpp/keywords-cpp.md)

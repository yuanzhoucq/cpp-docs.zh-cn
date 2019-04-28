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
ms.openlocfilehash: b9efac6f729a78db945ff3bd9ab16ebe315b7a5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266954"
---
# <a name="stdcall"></a>__stdcall

**Microsoft 专用**

**__Stdcall**调用约定用于调用 Win32 API 函数。 被调用方清理堆栈，因此编译器进行`vararg`函数 **__cdecl**。 使用此调用约定的函数需要一个函数原型。

## <a name="syntax"></a>语法

> *return-type* **\_\_stdcall** *function-name*[**(** *argument-list* **)**]

## <a name="remarks"></a>备注

以下列表显示此调用约定的实现。

|元素|实现|
|-------------|--------------------|
|参数传递顺序|从右到左。|
|参数传递约定|按值，除非传递指针或引用类型。|
|堆栈维护职责|调用的函数从堆栈中弹出自己的参数。|
|名称修饰约定|下划线 (_) 是名称的前缀。 名称后跟后面是自变量列表中的字节数（采用十进制）的符号 (@)。 因此，声明为 `int func( int a, double b )` 的函数按如下所示进行修饰：`_func@12`|
|大小写转换约定|None|

[/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md)编译器选项指定 **__stdcall**适用于使用不同的调用约定不显式声明的所有功能。

与以前版本的兼容性 **_stdcall**是的同义词 **__stdcall**除非编译器选项[/Za\(禁用语言扩展)](../build/reference/za-ze-disable-language-extensions.md)是指定。

使用声明的函数 **__stdcall**修饰符返回值声明使用的函数一样[__cdecl](../cpp/cdecl.md)。

在 ARM 和 x64 处理器， **__stdcall**接受和忽略由编译器; 在 ARM 和 x64 体系结构中，按照约定，参数将传入寄存器在可能的情况下，和后续自变量传递到堆栈上。

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

在以下示例中，利用 **__stdcall**会导致所有`WINAPI`函数类型作为标准调用处理：

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)<br/>
[关键字](../cpp/keywords-cpp.md)
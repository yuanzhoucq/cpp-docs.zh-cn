---
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: 298485d310ee4039b13781a8b5cd88a489af3b8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550210"
---
# <a name="cdecl"></a>__cdecl

**Microsoft 专用**

**__cdecl**是默认调用约定的 C 和 c + + 程序。 由调用方清理堆栈，因为它可以执行`vararg`函数。 **__Cdecl**调用约定创建更大的可执行文件比[__stdcall](../cpp/stdcall.md)，因为它要求每个函数调用包括堆栈清理代码。 以下列表显示此调用约定的实现。

|元素|实现|
|-------------|--------------------|
|自变量传递顺序|从右到左。|
|堆栈维护职责|调用函数从堆栈中弹出参数。|
|名称修饰约定|下划线字符 (_) 前缀的名称，除非当\_导出使用 C 链接的 _cdecl 函数。|
|大小写转换约定|不执行任何大小写转换。|

> [!NOTE]
>  有关相关信息，请参阅[修饰名](../build/reference/decorated-names.md)。

位置 **__cdecl**在变量或者函数名称前面的修饰符。 由于 C 命名和调用约定为默认值，时，才必须使用 **__cdecl**在 x86 代码是在指定`/Gv`(vectorcall)、 `/Gz` (stdcall) 或`/Gr`(fastcall)编译器选项。 [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md)编译器选项强制执行 **__cdecl**调用约定。

在 ARM 和 x64 处理器， **__cdecl**是接受，但编译器一般会忽略。 按照 ARM 和 x64 上的约定，自变量将尽可能传入寄存器，后续自变量传递到堆栈中。 在 x64 代码中，使用 **__cdecl**重写 **/Gv**编译器选项并使用默认的 x64 调用约定。

对于非静态类函数，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。 也就是说，对于类非静态成员方法，在定义时假定声明期间指定的调用约定。 给定此类定义：

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

此：

```cpp
void CMyClass::mymethod() { return; }
```

等效于此：

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

与以前版本的兼容性**cdecl**并 **_cdecl**是的同义词 **__cdecl**除非编译器选项[/Za\(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)指定。

## <a name="example"></a>示例

在下面的示例中，将指示编译器对 `system` 函数使用 C 命名和调用约定。

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)<br/>
[关键字](../cpp/keywords-cpp.md)
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
ms.openlocfilehash: b4a86c49880b0c40d402c7cec863f79e24bc4dc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371569"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl**是 C 和C++程序的默认调用约定。 由于堆栈由调用方清理，因此它可以执行`vararg`函数。 **__cdecl**调用约定创建比[__stdcall](../cpp/stdcall.md)更大的可执行文件，因为它需要每个函数调用来包含堆栈清理代码。 以下列表显示此调用约定的实现。 **__cdecl**修改器特定于 Microsoft。

|元素|实现|
|-------------|--------------------|
|参数传递顺序|从右到左。|
|堆栈维护职责|调用函数从堆栈中弹出自变量。|
|名称修饰约定|下划线字符 （*） 预指名称，\_但导出使用 C 链接的_cdecl函数除外。|
|大小写转换约定|不执行任何大小写转换。|

> [!NOTE]
> 有关相关信息，请参阅[修饰名称](../build/reference/decorated-names.md)。

将 **__cdecl**修改器放在变量或函数名称之前。 由于 C 命名和调用约定是默认值，因此在 x86 代码中必须使用 **__cdecl**的唯一时间是指定`/Gv`（矢量调用）、（stdcall）`/Gz`或`/Gr`（快速调用）编译器选项。 [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md)编译器选项强制 **__cdecl**调用约定。

在 ARM 和 x64 处理器上 **，__cdecl**被编译器接受，但通常忽略。 按照 ARM 和 x64 上的约定，自变量将尽可能传入寄存器，后续自变量传递到堆栈中。 在 x64 代码中，使用 **__cdecl**来重写 **/Gv**编译器选项并使用默认 x64 调用约定。

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

为了与早期版本兼容 **，cdecl**和 **_cdecl**是 **__cdecl**的同义词，除非指定编译器选项[/Za\(禁用语言扩展）。](../build/reference/za-ze-disable-language-extensions.md)

## <a name="example"></a>示例

在下面的示例中，将指示编译器对 `system` 函数使用 C 命名和调用约定。

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>另请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Keywords](../cpp/keywords-cpp.md)

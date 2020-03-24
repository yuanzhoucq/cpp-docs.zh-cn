---
title: code_seg (__declspec)
ms.date: 11/04/2016
f1_keywords:
- code_seg_cpp
helpviewer_keywords:
- code_seg __declspec keyword
ms.assetid: ad3c1105-15d3-4e08-b7b9-e4bd9d7b6aa0
ms.openlocfilehash: 22703e92b1a127378c965ce12bcc4e5475b3e452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180831"
---
# <a name="code_seg-__declspec"></a>code_seg (__declspec)

**Microsoft 专用**

**Code_seg**声明特性会将存储函数或类成员函数的对象代码的 .obj 文件中的可执行文本段命名为。

## <a name="syntax"></a>语法

```
__declspec(code_seg("segname")) declarator
```

## <a name="remarks"></a>备注

`__declspec(code_seg(...))` 特性可将代码放置到可在内存中独立分页或锁定的单独命名的段中。 你可以使用该特性控制实例化的模板和编译器生成的代码的放置位置。

*段*是作为一个单元加载到内存中的 .obj 文件中的命名数据块。 "*文本段*" 是包含可执行代码的段。 术语*部分*通常与段互换使用。

定义 `declarator` 时生成的对象代码将放入 `segname`（窄字符串字面值）指定的文本段。 不需要在[节](../preprocessor/section.md)杂注中指定名称 `segname`，就可以在声明中使用它。 默认情况下，未指定 `code_seg` 时，对象代码将放入名为 .text 的段中。 **Code_seg**特性会重写任何现有[#pragma code_seg](../preprocessor/code-seg.md)指令。 应用于成员函数的**code_seg**特性将重写应用于封闭类的任何**code_seg**特性。

如果实体具有**code_seg**属性，则同一实体的所有声明和定义必须具有相同的**code_seg**属性。 如果基类具有**code_seg**特性，派生类必须具有相同的特性。

将**code_seg**特性应用于命名空间范围函数或成员函数时，该函数的对象代码将放入指定的文本段中。 该特性应用于类时，类和嵌套类的所有成员函数（其中包括编译器生成的特殊成员函数）将放入指定段中。 本地定义的类（例如，成员函数主体中定义的类）不继承封闭范围的**code_seg**特性。

将**code_seg**特性应用到模板类或模板函数时，该模板的所有隐式专用化都将放入指定段中。 显式或部分专用化不从主模板继承**code_seg**特性。 你可以在专用化上指定相同的或不同的**code_seg**属性。 **Code_seg**特性不能应用于显式模板实例化。

默认情况下，编译器生成的代码（例如特殊成员函数）将放入 .text 段中。 `#pragma code_seg` 指令不重写该默认设置。 使用类、类模板或函数模板上的**code_seg**特性可以控制编译器生成的代码的放置位置。

Lambda 从其封闭范围继承**code_seg**特性。 若要为 lambda 指定段，请在参数声明子句之后以及任何可变或异常规范、任何尾随返回类型规范和 lambda 主体之前应用**code_seg**特性。 有关详细信息，请参阅[Lambda 表达式语法](../cpp/lambda-expression-syntax.md)。 该示例在名为 PagedMem 的段中定义 lambda：

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

在不同的段中放入特定成员函数（尤其是虚拟成员函数）时要特别小心。 如果你在位于分页段中的派生类中定义虚拟函数，而基类方法位于非分页段中，则其他基类方法或用户代码可能会假定调用该虚拟方法不会触发页面错误。

## <a name="example"></a>示例

此示例演示如何在使用隐式和显式模板专用化时， **code_seg**属性如何控制段放置：

```cpp
// code_seg.cpp
// Compile: cl /EHsc /W4 code_seg.cpp

// Base template places object code in Segment_1 segment
template<class T>
class __declspec(code_seg("Segment_1")) Example
{
public:
   virtual void VirtualMemberFunction(T /*arg*/) {}
};

// bool specialization places code in default .text segment
template<>
class Example<bool>
{
public:
   virtual void VirtualMemberFunction(bool /*arg*/) {}
};

// int specialization places code in Segment_2 segment
template<>
class __declspec(code_seg("Segment_2")) Example<int>
{
public:
   virtual void VirtualMemberFunction(int /*arg*/) {}
};

// Compiler warns and ignores __declspec(code_seg("Segment_3"))
// in this explicit specialization
__declspec(code_seg("Segment_3")) Example<short>; // C4071

int main()
{
   // implicit double specialization uses base template's
   // __declspec(code_seg("Segment_1")) to place object code
   Example<double> doubleExample{};
   doubleExample.VirtualMemberFunction(3.14L);

   // bool specialization places object code in default .text segment
   Example<bool> boolExample{};
   boolExample.VirtualMemberFunction(true);

   // int specialization uses __declspec(code_seg("Segment_2"))
   // to place object code
   Example<int> intExample{};
   intExample.VirtualMemberFunction(42);
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)

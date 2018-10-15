---
title: 数组 (C + + /cli 和 C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b1a1f977e15d80d631799d8a9e101a8c85e3aaf1
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328098"
---
# <a name="arrays-ccli-and-ccx"></a>数组 (C + + /cli 和 C + + /cli CX)

`Platform::Array<T>`类型在 C + + /CX 中，或**数组**关键字在 C + + /cli CLI，声明数组的指定的类型和初始值。

## <a name="all-platforms"></a>所有平台

必须通过在右尖括号 (>) 中声明后使用句柄到对象 (^) 修饰符声明数组。
数组的元素数不是该类型的一部分。 一个数组变量可以引用不同大小的数组。

与不同的是标准 c + +，下标不用于指针算术的同义词，具有不可交换性。

有关数组的详细信息，请参阅：

- [如何：在 C++/CLI 中使用数组](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [变量自变量列表 (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows 运行时

数组是成员的`Platform`命名空间。 数组可以是仅一维。

### <a name="syntax"></a>语法

第一个语法的示例使用**ref 新**聚合关键字分配一个数组。 第二个示例声明本地数组。

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}
```

*限定符*<br/>
（可选）一个或多个这些存储类说明符：[可变](../cpp/mutable-data-members-cpp.md)，[易失性](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)，[静态](../cpp/static-members-cpp.md).

*数组类型*<br/>
数组变量的类型。 有效类型为 Windows 运行时类和基本类型、 ref 类和结构、 值类和结构和本机指针 (`type*`)。

*rank*<br/>
（可选）数组的维度数。 必须为 1。

*identifier*<br/>
数组变量的名称。

*初始化类型*<br/>
初始化数组的值的类型。 通常情况下，*数组类型*并*初始化类型*属于同一类型。 但是，类型可以是不同的转换是否*初始化类型*到*数组类型*— 例如，如果*初始化类型*派生自*数组类型*。

*初始化列表*<br/>
（可选）以逗号分隔列表中初始化数组的元素的大括号的值。 例如，如果*排名大小列表*已`(3)`，其中声明了 3 个元素的一维数组*初始化列表*可能是`{1,2,3}`。

### <a name="remarks"></a>备注

您可以在编译时检测类型是否是类型的引用计数数组`__is_ref_array(type)`。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

### <a name="examples"></a>示例

以下示例创建具有 100 个元素的一维数组。

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="syntax"></a>语法

第一个语法的示例使用**gcnew**关键字来分配一个数组。 第二个示例声明本地数组。

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}
```

*限定符*<br/>
（可选）一个或多个这些存储类说明符：[可变](../cpp/mutable-data-members-cpp.md)，[易失性](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)，[静态](../cpp/static-members-cpp.md).

*数组类型*<br/>
数组变量的类型。 有效类型是 Windows 运行时类和基本类型，ref 类和结构、 值类和结构，本机指针 (`type*`)，和 POD （纯旧数据） 的本机类型。

*rank*<br/>
（可选）数组的维度数。 默认值为 1;最大值为 32。 每个维度本身就是数组的一个数组。

*identifier*<br/>
数组变量的名称。

*初始化类型*<br/>
初始化数组的值的类型。 通常情况下，*数组类型*并*初始化类型*属于同一类型。 但是，类型可以是不同的转换是否*初始化类型*到*数组类型*— 例如，如果*初始化类型*派生自*数组类型*。

*排名大小列表*<br/>
以逗号分隔的数组中每个维度的大小的列表。 或者，如果*初始化列表*指定为参数时，编译器可以推断出的每个维度的大小和*排名大小列表*可以省略。

*初始化列表*<br/>
（可选）以逗号分隔列表中初始化数组的元素的大括号的值。 或以逗号分隔列表的嵌套*初始化列表*初始化多维数组中的元素的项。

例如，如果*排名大小列表*已`(3)`，其中声明了 3 个元素的一维数组*初始化列表*可能是`{1,2,3}`。 如果*排名大小列表*已`(3,2,4)`，该声明的第一个维度、 2 个元素在第二个和第三个中的 4 个元素中的 3 个元素的三维数组*初始化列表*可能是`{{1,2,3},{0,0},{-5,10,-21,99}}`。)

### <a name="remarks"></a>备注

**数组**处于[Platform、 default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)命名空间。

如标准 c + +，数组的索引是从零开始，并且数组下标使用方括号 ([])。 与不同的是标准 c + +，而不是一组方括号 ([]) 运算符，为每个维度的每个维度的索引的列表中指定的多维数组的索引。 例如，*标识符*[*index1*， *index2*] 而不是*标识符*[*index1*] [ *index2*]。

所有托管的数组继承`System::Array`。 任何方法或属性的`System::Array`可以直接应用于数组变量。

当您分配一个数组，其元素类型为指针的托管类的元素是 0 初始化。

当您分配一个数组，其元素类型是值类型`V`的默认构造函数`V`应用于每个数组元素。 有关详细信息，请参阅[对应于 c + + 本机类型的.NET Framework (C + + CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。

在编译时，可以检测是否使用的公共语言运行时 (CLR) 数组类型`__is_ref_array(type)`。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

以下示例创建具有 100 个元素的一维数组和一个三维数组具有 3 个元素中的第一个维度、 5 个元素在第二个和第三个中的 6 个元素。

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>请参阅

[适用于.NET 和 UWP 组件扩展](../windows/component-extensions-for-runtime-platforms.md)
---
title: array（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: e4173c16e13c08a54b36e42183e6e18b6ed4fdc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516192"
---
# <a name="arrays-ccli-and-ccx"></a>array（C++/CLI 和 C++/CX）

C++/CX 中的 `Platform::Array<T>` 类型或 C++/CLI 中的 array 关键字声明了，具有指定类型和初始值的数组。

## <a name="all-platforms"></a>所有平台

必须在声明中的右尖括号 (>) 后面使用指向对象的句柄 (^) 修饰符来声明数组。
数组的元素数不是类型的一部分。 一个数组变量可以引用多个不同大小的数组。

与标准 C++ 不同，下标不是指针算术运算的同义词，且不可交换。

若要详细了解数组，请参阅：

- [如何：在 C++/CLI 中使用数组](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [变量自变量列表 (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows 运行时

数组是 `Platform` 命名空间的成员。 数组只能是一维的。

### <a name="syntax"></a>语法

第一个语法示例使用 ref new 聚合关键字来分配数组。 第二个示例声明本地数组。

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

qualifiers<br/>
（可选）下面这些存储类说明符中的一个或多个：[mutable](../cpp/mutable-data-members-cpp.md)、[volatile](../cpp/volatile-cpp.md)、[const](../cpp/const-cpp.md)、[extern](../cpp/using-extern-to-specify-linkage.md)、[static](../cpp/static-members-cpp.md)。

array-type<br/>
数组变量的类型。 有效类型为 Windows 运行时类和基本类型、ref class 和 ref struct、value class 和 value struct 以及本机指针 (`type*`)。

*rank*<br/>
（可选）数组的维数。 必须为 1。

*identifier*<br/>
数组变量的名称。

initialization-type<br/>
初始化数组的值的类型。 通常情况下，array-type 和 initialization-type 的类型相同。 不过，如果从 initialization-type 转换为 array-type（例如，如果 initialization-type 派生自 array-type），类型可能会不同。

initialization-list<br/>
（可选）用大括号括起来的逗号分隔值列表，用于初始化数组元素。 例如，如果 rank-size-list 为 `(3)`（即声明由 3 个元素组成的一维数组），initialization-list 可以是 `{1,2,3}`。

### <a name="remarks"></a>备注

在编译时，可以使用 `__is_ref_array(type)` 来检测类型是否是引用计数数组。 有关详细信息，请参阅[编译器对类型特征的支持](compiler-support-for-type-traits-cpp-component-extensions.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

### <a name="examples"></a>示例

下面的示例创建由 100 个元素组成的一维数组。

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

第一个语法示例使用 gcnew 关键字来分配数组。 第二个示例声明本地数组。

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

qualifiers<br/>
（可选）下面这些存储类说明符中的一个或多个：[mutable](../cpp/mutable-data-members-cpp.md)、[volatile](../cpp/volatile-cpp.md)、[const](../cpp/const-cpp.md)、[extern](../cpp/using-extern-to-specify-linkage.md)、[static](../cpp/static-members-cpp.md)。

array-type<br/>
数组变量的类型。 有效类型为 Windows 运行时类和基本类型、ref class 和 ref struct、value class 和 value struct、本机指针 (`type*`) 以及本机 POD（纯旧数据）类型。

*rank*<br/>
（可选）数组的维数。 默认值为 1；最大值为 32。 数组的每个维度本身都是一个数组。

*identifier*<br/>
数组变量的名称。

initialization-type<br/>
初始化数组的值的类型。 通常情况下，array-type 和 initialization-type 的类型相同。 不过，如果从 initialization-type 转换为 array-type（例如，如果 initialization-type 派生自 array-type），类型可能会不同。

rank-size-list<br/>
数组中每个维度的大小的逗号分隔列表。 另外，如果 initialization-list 参数已指定，编译器可以推导每个维度的大小，而且 rank-size-list 也能省略。

initialization-list<br/>
（可选）用大括号括起来的逗号分隔值列表，用于初始化数组元素。 或嵌套 initialization-list 项的逗号分隔列表，用于初始化多维数组中的元素。

例如，如果 rank-size-list 为 `(3)`（即声明由 3 个元素组成的一维数组），initialization-list 可以是 `{1,2,3}`。 如果 rank-size-list 为 `(3,2,4)`（即声明一个三维数组，第一个维度中有 3 个元素，第二个维度中有 2 个元素，第三个维度中有 4 个元素），initialization-list 可以是 `{{1,2,3},{0,0},{-5,10,-21,99}}`。

### <a name="remarks"></a>备注

array 位于[平台默认 cli 命名空间](platform-default-and-cli-namespaces-cpp-component-extensions.md)中。

与标准 C++ 一样，数组的索引也是从零开始编制，且数组使用方括号 ([]) 作为下标。 与标准 C++ 不同，多维数组的索引是在每个维度的索引列表中指定，而不是对每个维度使用一组方括号 ([]) 运算符。 例如，identifier[index1, index2]，而不是 identifier[index1][index2]。

所有托管数组都继承自 `System::Array`。 `System::Array` 的任何方法或属性都可以直接应用于数组变量。

如果你分配的数组的元素类型为指向托管类的指针，元素初始化为 0。

如果你分配的数组的元素类型为值类型 `V`，`V` 的默认构造函数会应用于每个数组元素。 有关详细信息，请参阅[相当于 C++ 本机类型的 .NET Framework 类型 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。

在编译时，可以使用 `__is_ref_array(type)` 来检测类型是否是公共语言运行时 (CLR) 数组。 有关详细信息，请参阅[编译器对类型特征的支持](compiler-support-for-type-traits-cpp-component-extensions.md)。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例创建由 100 个元素组成的一维数组，以及第一个维度中有 3 个元素、第二个维度中有 5 个元素、第三个维度中有 6 个元素的三维数组。

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

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
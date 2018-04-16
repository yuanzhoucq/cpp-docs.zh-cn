---
title: "数组 （c + + 组件扩展） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
- declaring arrays, about declaring arrays
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 343f2369260531e828ea8db27cee5e52ea18fd31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="arrays-c-component-extensions"></a>数组（C++ 组件扩展）
`Platform::Array<T>`类型在 C + + /CX 中，或`array`关键字在 C + + /cli CLI，声明的指定的类型和初始值的数组。  
  
## <a name="all-platforms"></a>所有平台  
 必须使用后在右尖括号 (>) 声明中的句柄到对象 (^) 修饰符声明数组。  
 数组的元素的数目不是类型的一部分。 一个数组变量可引用不同的大小的数组。  
  
 不同于标准 c + +，下标不是指针算术的同义词，并不是可交换。  
  
 有关数组的详细信息，请参阅：  
  
-   [如何：在 C++/CLI 中使用数组](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
    
-   [变量自变量列表 (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Windows 运行时  
 数组是的成员`Platform`命名空间。 数组可以是仅一维。  
  
### <a name="syntax"></a>语法  
  
 语法的第一个示例使用`ref new`聚合关键字分配一个数组。 第二个示例声明的本地数组。  
  
```  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *限定符*[可选]  
 一个或多个这些存储类说明符：[可变](../cpp/mutable-data-members-cpp.md)，[易失性](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)，[静态](../cpp/static-members-cpp.md).  
  
 `array-type`  
 数组变量的类型。 有效类型为 Windows 运行时类和基本类型、 ref 类和结构、 值类和结构和本机指针 (`type*`)。  
  
 `rank`[可选]  
 数组的维度数。 必须为 1。  
  
 `identifier`  
 数组变量的名称。  
  
 `initialization-type`  
 初始化该数组的值的类型。 通常情况下，`array-type`和`initialization-type`具有相同的类型。 但是，类型可以是不同的转换是否`initialization-type`到`array-type`— 例如，如果`initialization-type`派生自`array-type`。  
  
 `initialization-list`[可选]  
 以逗号分隔初始化数组的元素的大括号中的值的列表。 例如，如果`rank-size-list`已`(3)`，该声明的 3 个元素，一维数组`initialization list`可能是`{1,2,3}`。  
  
### <a name="remarks"></a>备注  
  
 你可以在编译时检测类型是否是类型的引用计数数组`__is_ref_array(type)`。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
### <a name="examples"></a>示例  
 下面的示例创建一个有 100 个元素的一维数组。  
  
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
  
 语法的第一个示例使用`gcnew`关键字来分配一个数组。 第二个示例声明的本地数组。  
  
```  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *限定符*[可选]  
 一个或多个这些存储类说明符：[可变](../cpp/mutable-data-members-cpp.md)，[易失性](../cpp/volatile-cpp.md)， [const](../cpp/const-cpp.md)， [extern](../cpp/using-extern-to-specify-linkage.md)，[静态](../cpp/static-members-cpp.md).  
  
 `array-type`  
 数组变量的类型。 有效类型为 Windows 运行时类和基本类型、 ref 类和结构、 值类和结构，本机指针 (`type*`)，和本机的 POD （纯旧数据） 类型。  
  
 `rank`[可选]  
 数组的维度数。 默认值为 1;最大值为 32。 每个维度本身就是数组的一个数组。  
  
 `identifier`  
 数组变量的名称。  
  
 `initialization-type`  
 初始化该数组的值的类型。 通常情况下，`array-type`和`initialization-type`具有相同的类型。 但是，类型可以是不同的转换是否`initialization-type`到`array-type`— 例如，如果`initialization-type`派生自`array-type`。  
  
 `rank-size-list`  
 以逗号分隔列表的数组中每个维度的大小。 或者，如果`initialization-list`指定参数，编译器可以推断出的每个维度的大小和`rank-size-list`可以省略。 
  
 `initialization-list`[可选]  
 以逗号分隔初始化数组的元素的大括号中的值的列表。 或逗号分隔的列表嵌套*初始化列表*初始化多维数组中的元素的项。  
  
 例如，如果`rank-size-list`已`(3)`，该声明的 3 个元素，一维数组`initialization list`可能是`{1,2,3}`。 如果`rank-size-list`已`(3,2,4)`，其声明中的第一个维度、 2 个元素在第二个和 4 个元素中第三个、 3 个元素的三维数组`initialization-list`可能是`{{1,2,3},{0,0},{-5,10,-21,99}}`。)  
  
### <a name="remarks"></a>备注  
  
 `array`处于[平台、 default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)命名空间。  
  
 标准 c + +，如数组的索引是从零开始，和数组下标通过使用方括号 ([])。 与标准 c + +，不同的多维数组索引指定列表中的每个维度而不是一组方括号 ([]) 运算符时针对每个维度的索引。 例如，*标识符*[*index1*， *index2*] 而不是*标识符*[*index1*] [ *index2*]。  
  
 所有托管的数组继承`System::Array`。 任何方法或属性的`System::Array`可以将直接应用到的数组变量。  
  
 当你分配一个数组，其元素类型为指针的托管类的元素将 0 初始化。  
  
 当你分配一个数组，其元素类型是值类型`V`的默认构造函数`V`应用于每个数组元素。 有关详细信息，请参阅[到 c + + 本机类型的.NET Framework 等效项 (C + + /cli CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。  
  
 在编译时，你可以检测是否不包含的公共语言运行时 (CLR) 数组类型`__is_ref_array(type)`。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 下面的示例创建有 100 个元素的一维数组和一个三维数组具有 3 个元素中的第一个维度、 在第二个，5 个元素和 6 在第三个元素。  
  
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
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
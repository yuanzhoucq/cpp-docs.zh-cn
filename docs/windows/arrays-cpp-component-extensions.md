---
title: "数组（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "cli::array"
  - "details::array"
  - "lang::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array 关键字 [C++]"
  - "数组 [C++]"
  - "数组 [C++], 多维"
  - "声明数组, 关于声明数组"
  - "多维数组"
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数组（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

输入 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)]，`Platform::Array<T>` 或 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)]中的 `array` 关键字，声明一个指定类型值和原始值的。  
  
## 所有平台  
 必须声明数组使用句柄到对象 \(^\) 修饰符。结束的尖括号 \(\>\) 之后声明中。  
  
 数组元素的数目不为类型的一部分。  一种数组变量可以引用不同的大小。  
  
 与标准 C\+\+，下标不是指针算法的同义词不可交换的。  
  
 有关数组的更多信息，请参见 ：  
  
-   [数组协方差](../misc/array-covariance.md)  
  
-   [如何：在 C\+\+\/CLI 中使用数组](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
  
-   [如何：创建多维数组](../misc/how-to-create-multidimension-arrays.md)  
  
-   [如何：创建托管数组的数组（交错数组）](../misc/how-to-create-arrays-of-managed-arrays-jagged-arrays.md)  
  
-   [如何：为托管数组创建 Typedefs](../misc/how-to-make-typedefs-for-managed-arrays.md)  
  
-   [如何：将托管数组用作模板类型参数](../misc/how-to-use-managed-arrays-as-template-type-parameters.md)  
  
-   [变量参数列表 \(...\) \(C\+\+\/CLI\)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
-   [如何：对数组进行排序](../misc/how-to-sort-arrays.md)  
  
-   [如何：使用自定义条件对数组进行排序](../misc/how-to-sort-arrays-using-custom-criteria.md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 `Platform` 命名空间的类型和成员。  数组只能一维。  
  
 **语法**  
  
 语法中的第一个示例使用 `ref new` 聚合关键字分配数组。  第二个示例声明局部数组。  
  
```  
  
        [qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = ref new [Platform::]Array< initialization-type > [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = {initialization-list [,...]}  
  
```  
  
 *qualifiers* （可选）  
 一个或多个这些存储类说明符：[mutable](../cpp/mutable-data-members-cpp.md)，[变量](../cpp/volatile-cpp.md)，[const](../cpp/const-cpp.md)，[外部](../cpp/using-extern-to-specify-linkage.md)，[静态的](../misc/static-cpp.md)。  
  
 `array-type`  
 数组的元素类型。  有效的类型是 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 类以及基础类型、ref 类和值类、结构和结构的本机指针 \(`type``*`\)。  
  
 `rank`（可选）  
 数组的维数。  必须为 1。  
  
 `identifier`  
 窗体变量的名称。  
  
 `initialization-type`  
 初始化数组值的类型。  通常，`array-type` 和 `initialization-type` 是相同类型。  但是，类型可以不同，如果有从 `initialization-type` 到 `array-type`的转换\) 的示例，因此，如果 `initialization-type` 从 `array-type`派生。  
  
 `initialization-list`（可选）  
 逗号分隔值列表。初始化数组的元素花括号的。  例如，在中，如果 `rank-size-list` 为 `(3)`，声明一维数组元素 3，`initialization list` 可以为 `{1,2,3}`。  
  
 **备注**  
  
 可以检测编译时类型是否与 `__is_ref_array(``type``)`的引用计数的数组。  有关详细信息，请参阅[编译器使用类型特征支持](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
### 要求  
 编译器选项：**\/ZW**  
  
### 示例  
 下面的示例将创建具有 100 个元素的一维数组。  
  
```  
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
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **语法**  
  
 语法中的第一个示例使用 `gcnew` 聚合关键字分配数组。  第二个示例声明局部数组。  
  
```  
  
        [qualifiers] [cli::]array<[qualifiers] array-type [,rank] >^ identifier = gcnew [cli::]array< initialization-type [,rank] >(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank] >^ identifier = {initialization-list [,...]}  
  
```  
  
 *qualifiers* （可选）  
 一个或多个这些存储类说明符：[mutable](../cpp/mutable-data-members-cpp.md)，[变量](../cpp/volatile-cpp.md)，[const](../cpp/const-cpp.md)，[外部](../cpp/using-extern-to-specify-linkage.md)，[静态的](../misc/static-cpp.md)。  
  
 `array-type`  
 数组的元素类型。  有效的类型是 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 类以及基础类型、ref 类和结构、值类和结构、本机指针 \(`type``*`\) 和本机 POD \(纯旧数据\) 类型。  
  
 `rank`（可选）  
 数组的维数。  默认为 1;最大值为 32。  数组的每个维度本身是数组。  
  
 `identifier`  
 窗体变量的名称。  
  
 `initialization-type`  
 初始化数组值的类型。  通常，`array-type` 和 `initialization-type` 是相同类型。  但是，类型可以不同，如果有从 `initialization-type` 到 `array-type`的转换\) 的示例，因此，如果 `initialization-type` 从 `array-type`派生。  
  
 `rank-size-list`  
 每个维度的大小的逗号分隔列表的数组中。  或者，如果 `initialization-list` 参数指定，编译器可以推导出每一维的大小，`rank-size-list` 可以省略。  有关详细信息，请参阅[如何：创建多维数组](../misc/how-to-create-multidimension-arrays.md)。  
  
 `initialization-list`（可选）  
 逗号分隔值列表。初始化数组的元素花括号的。  或者初始化在一个多维数组的元素嵌套的 *initialization\-list* 项的逗号分隔列表。  
  
 例如，在中，如果 `rank-size-list` 为 `(3)`，声明一维数组元素 3，`initialization list` 可以为 `{1,2,3}`。  如果 `rank-size-list` 为 `(3,2,4)`，3 元素声明一个三维数组中第一个维中的元素 2，在第二个和第三个 4 元素，`initialization-list` 可能是 `{{1,2,3},{0,0},{-5,10,-21,99}}`。\)  
  
 **备注**  
  
 `array` 是[Platform、default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)命名空间中的类型。  
  
 与标准 C\+\+，数组索引从零开始，所以，数组就 subscripted 使用方括号 \(\[\]\)。  与标准 C\+\+，一种多维数组的索引。索引列表指定为每一维而非一组正方形括号 \(\[\]\) 运算符为每一维。  例如，*identifier*\[*index1*, *index2*\]替代为 *identifier*\[*index1*\]\[ *index2*\]  
  
 所有托管数组从 `System::Array`继承。  所有 `System::Array` 方法或属性可直接应用于数组变量。  
  
 当您分配元素类型为指针对托管类的数组时，元素 0 初始化。  
  
 当您分配元素类型就是"值类型 `V`的数组时，`V` 的默认构造函数应用于数组的每个元素。  有关详细信息，请参阅[对应于 C\+\+ 本机类型的 .NET Framework 类型](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。  
  
 在编译时，可以检测类型是否与 `__is_ref_array(``type``)`的公共语言运行时 \(CLR\) \(CLR\) 数组。  有关详细信息，请参阅[编译器使用类型特征支持](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 下面的示例将创建具有 100 个元素的一维数组和包含 3 个元素。第一个维的一个"三维数组中的元素 5，第二个和第三个 6 个元素。  
  
```  
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
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
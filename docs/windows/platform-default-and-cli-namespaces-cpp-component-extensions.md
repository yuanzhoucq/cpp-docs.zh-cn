---
title: 平台、 default 和 cli 命名空间 （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- lang
- cli
dev_langs:
- C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b466a94aba9f19907a5438a8b8e623d65aa0ac2d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="platform-default-and-cli-namespaces--c-component-extensions"></a>Platform、default 和 cli 命名空间（C++ 组件扩展）
命名空间限定语言元素的名称，使这些名称不与源代码中其他位置的相同名称发生冲突。 例如，名称冲突可能会阻止编译器识别[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。 命名空间由编译器使用但不保留在已编译的程序集中。  
  
## <a name="all-runtimes"></a>所有运行时  
 创建项目时，Visual C++ 为项目提供默认命名空间。 尽管在 Windows 运行时的.winmd 文件的名称必须与匹配的根命名空间的名称，可以手动重命名命名空间。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 有关详细信息，请参阅[命名空间和类型可见性 (C + + /cli CX)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx)。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **语法**  
  
```  
using namespace cli;  
```  
  
 **备注**  
  
 C + + /cli CLI 支持`cli`命名空间。 使用编译时 **/clr**、`using`默示语法部分中的语句。  
  
 以下语言功能位于 `cli` 命名空间中：  
  
-   [数组](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 以下代码示例表明可以将 `cli` 命名空间中的符号用作你代码中的用户定义符号。  但是，一旦执行此操作，你必须显式或隐式限定你对具有相同名称的 `cli` 语言元素的引用。  
  
```  
// cli_namespace.cpp  
// compile with: /clr  
using namespace cli;  
int main() {  
   array<int> ^ MyArray = gcnew array<int>(100);  
   int array = 0;  
  
   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062  
  
   // OK  
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);  
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
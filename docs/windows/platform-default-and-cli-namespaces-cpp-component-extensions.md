---
title: "Platform、default 和 cli 命名空间（C++ 组件扩展） | Microsoft Docs"
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
  - "lang"
  - "cli"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cli 命名空间"
  - "lang 命名空间"
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Platform、default 和 cli 命名空间（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命名空间限定语言元素的名称，使这些名称不与源代码中其他位置的相同名称发生冲突。  例如，名称冲突可能会阻止编译器识别[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  命名空间由编译器使用但不保留在已编译的程序集中。  
  
## 所有运行时  
 创建项目时，Visual C\+\+ 为项目提供默认命名空间。  可以手动重命名此命名空间，但在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]中，.winmd 文件的名称必须与根命名空间的名称匹配。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 有关详细信息，请参阅[命名空间和类型可见性 \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx)。  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **语法**  
  
```  
using namespace cli;  
```  
  
 **备注**  
  
 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] 支持 `cli` 命名空间。  使用 **\/clr** 进行编译时，将在“语法”部分暗示 `using` 语句。  
  
 以下语言功能位于 `cli` 命名空间中：  
  
-   [数组](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)  
  
-   [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
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
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)
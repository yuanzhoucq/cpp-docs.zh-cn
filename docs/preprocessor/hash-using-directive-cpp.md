---
title: "#using 指令 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "friend_as_cpp"
  - "#using"
  - "friend_as"
  - "#using_cpp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#using 指令"
  - "LIBPATH 环境变量"
  - "预处理器, 指令"
  - "using 指令 (#using)"
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #using 指令 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)将元数据导入程序编译。  
  
## 语法  
  
```  
#using file [as_friend]  
```  
  
#### 参数  
 `file`  
 MSIL .dll、.exe、.netmodule 或 .obj。  例如，  
  
 `#using <MyComponent.dll>`  
  
 as\_friend  
 指定所有类型 `file` 都是可访问的。有关详细信息，请参阅[友元程序集 \(C\+\+\)](../dotnet/friend-assemblies-cpp.md)。  
  
## 备注  
 `file` 可以是您为其托管数据导入和管理构造的 microsoft 中间语言 \(msil\) 文件。  如果 .dll 文件包含一个程序集清单，则导入清单中引用的所有 .dll，并将生成的程序集和在元数据 *file* 为程序集引用。  
  
 如果 `file` 不包含程序集 \(如果 `file` 是模块\)，并且，如果您在当前 \(程序集\) 应用程序不想使用从模块的类型信息，则具有清单的选项模块作为部分程序集；使用 [\/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。  模块中的类型和被引用程序集的对所有应用程序都可用。  
  
 使用`#using` 的替代项为 [\/FU](../build/reference/fu-name-forced-hash-using-file.md) 编译器选项。  
  
 将生成的 .exe 程序传递给 `#using` 应当被 **\/clr:safe** 或 **\/clr:pure**编译，或者与其他任意的 Visual Studio 编译器 \(如：Visual Basic 或 Visual C\#\)。试图从 .exe 程序集导入元数据编译 **\/clr** 将会导致文件加载异常。  
  
> [!NOTE]
>  使用引用 `#using` 的元素可以运行带有文件的不同版本导入在编译时，导致客户端应用程序产生意外的结果。  
  
 为了让编译器识别出程序集中的类型（而不是模块），需要强制解析类型，例如可以通过定义此类型的实例来完成。  也有其他方法来为编译器解析程序集中的类型名称，例如，如果从一个程序集的类型继承，编译器就会知道此类型名称。  
  
 当导入生成的元数据使用 [\_\_declspec\(thread\)](../cpp/thread.md)中的源代码，线程语义在元数据不会保留。  例如，通过 `#using`声明 **\_\_declspec\(thread\)**，生成将作为 .NET Framework 公共语言运行时生成的程序，然后导入的变量，将不再具有在变量中 **\_\_declspec\(thread\)** 语义。  
  
 所有导入的类型 \(管理和本机\) 在 `#using` 引用的文件可用，但是，编译器将本机类型作为不是声明定义。  
  
 在使用编译 **\/clr**时，mscorlib.dll 自动引用。  
  
 LIBPATH 环境变量指定要搜索的目录，则编译器尝试解析文件名并传递给 `#using`。  
  
 编译器将沿下列路径搜索引用：  
  
-   在 `#using` 语句中指定的路径。  
  
-   当前目录。  
  
-   .NET Framework 系统目录。  
  
-   从目录添加与 [\/AI](../build/reference/ai-specify-metadata-directories.md) 编译器选项。  
  
-   在 LIBPATH 环境变量的目录。  
  
## 示例  
 如果您生成程序集 \(c\) 和引用自身引用其他程序集的程序集 \(b\)，您不需要显式引用程序集 A，除非您显式使用一个来输入 C。  
  
```  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## 示例  
  
```  
// using_assembly_B.cpp  
// compile with: /clr /LD  
#using "using_assembly_A.dll"  
public ref class B {  
public:  
   void Test(A a) {}  
   void Test() {}  
};  
  
```  
  
## 示例  
 在下面的示例中，因为程序在 using\_assembly\_A.cpp，不使用定义的任何一个类型不引用的 using\_assembly\_A.dll 编译器错误。  
  
```  
// using_assembly_C.cpp  
// compile with: /clr  
#using "using_assembly_B.dll"  
int main() {  
   B b;  
   b.Test();  
}  
```  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)
---
title: "#using 指令 (C + + /cli CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs: C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8a73eb8e9b5c3f3ba67e4466a6e7138010fd430
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-directive-cclr"></a>#using 指令 (C + + /cli CLR)
将元数据导入编译的程序[/clr](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="syntax"></a>语法  
  
```  
#using file [as_friend]  
```  
  
#### <a name="parameters"></a>参数  
 `file`  
 MSIL .dll、.exe、.netmodule 或 .obj。例如，应用于对象的  
  
 `#using <MyComponent.dll>`  
  
 as_friend  
 指定 `file` 中的所有类型都是可访问的。  有关详细信息，请参阅[友元程序集 （c + +）](../dotnet/friend-assemblies-cpp.md)。  
  
## <a name="remarks"></a>备注  
 `file` 可以是您为其托管数据和托管结构导入的 Microsoft 中间语言 (MSIL) 文件。 如果.dll 文件包含程序集清单，则导入清单中引用的所有.dll 和要生成的程序集将列出*文件*作为程序集引用的元数据中。  
  
 如果`file`不包含程序集 (如果`file`是一个模块); 如果不打算使用当前 （程序集） 应用程序中的模块中的类型信息，我们可以选择指示模块一部分的程序集; 请改用[进行](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。 然后，模块中的类型将可用于引用此程序集的任何应用程序。  
  
 若要使用的替代方法`#using`是[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项。  
  
 .exe 程序集传递到`#using`应编译使用.NET Visual Studio 编译器 （Visual Basic 或 Visual C# 中，例如） 之一。  尝试从使用编译的.exe 程序集导入元数据**/clr**将导致文件加载异常。  
  
> [!NOTE]
>  使用 `#using` 引用的组件可与编译时导入的文件的其他版本一起运行，这会导致客户端应用程序产生意外结果。  
  
 为了使让编译器识别出的程序集 （而不是模块） 中的类型，它需要强制解析类型，你可以执行此操作，例如，通过定义类型的实例。 如果从程序集中的类型继承，没有其他的方法可以解决对于编译器，例如，程序集的类型名称，类型名称就会知道到编译器。  
  
 导入从使用的源代码生成的元数据时[__declspec （thread)](../cpp/thread.md)，线程语义不会保留在元数据中。 例如，与声明的变量**__declspec （thread)**为.NET Framework 公共语言运行时，生成，然后通过导入的程序中编译`#using`，将不再有**__declspec (线程）**对变量的语义。  
  
 `#using` 引用的文件中所有导入的类型（托管的和本机的）都是可用的，但编译器会将本机类型视为声明而不是定义。  
  
 使用编译时，将自动引用 mscorlib.dll **/clr**。  
  
 LIBPATH 环境变量指定在编译器尝试解析传递给 `#using` 的文件名时要搜索的目录。  
  
 编译器将沿以下路径搜索引用：  
  
-   `#using` 语句中指定的路径。  
  
-   当前目录中。  
  
-   .NET Framework 系统目录。  
  
-   使用添加的目录[/AI](../build/reference/ai-specify-metadata-directories.md)编译器选项。  
  
-   LIBPATH 环境变量上的目录。  
  
## <a name="example"></a>示例  
 如果您生成程序集 (C) 并引用自身引用其他程序集 (A) 的程序集 (B)，则不需要显式引用程序集 A，除非您在 C 中显式使用 A 的某个类型。  
  
```  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## <a name="example"></a>示例  
  
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
  
## <a name="example"></a>示例  
 在下面的示例中，没有因不引用 using_assembly_A.dll 而导致的编译器错误，因为此程序不使用在 using_assembly_A.cpp 中定义的任一类型。  
  
```  
// using_assembly_C.cpp  
// compile with: /clr  
#using "using_assembly_B.dll"  
int main() {  
   B b;  
   b.Test();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)
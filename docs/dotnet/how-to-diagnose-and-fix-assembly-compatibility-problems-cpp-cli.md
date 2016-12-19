---
title: "如何：诊断和修复程序集兼容性问题 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "兼容性, 程序集之间"
  - "异常, 诊断异常行为"
  - "版本"
  - "版本, 诊断冲突"
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：诊断和修复程序集兼容性问题 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此主题说明编译时引用的程序集版本与运行时引用的程序集版本不匹配时可能发生的问题，以及如何避免该问题。  
  
 编译程序集时，可能使用 `#using` 语法引用其他程序集。  在编译过程中，这些程序集由编译器访问。  来自这些程序集的信息用于进行优化决策。  
  
 然而，如果更改并重新编译了被引用的程序集，而没有重新编译依赖它的引用程序集，则这些程序集可能不再是兼容的。  起初有效的优化决策对于新的程序集版本来说可能是不正确的。  这些不兼容性可能导致各种运行时错误。  在这种情况下，将不产生任何特定异常。  在运行时报告失败的方式取决于导致问题的代码更改的性质。  
  
 只要为产品的已发布版本重新生成了整个应用程序，这些错误在您最终的生产代码中应该不会成为问题。  公开发布的程序集应使用正式版本号标记，这将确保避免这些问题。  有关详细信息，请参阅[程序集版本控制](../Topic/Assembly%20Versioning.md)。  
  
### 诊断和修复不兼容性错误  
  
1.  如果遇到在引用其他程序集的代码中发生运行时异常或其他错误条件，并且找不出其他原因，则您可能正在使用过期的程序集。  
  
2.  首先，隔离并再现异常或其他错误条件。  过期异常导致的问题应该是可再现的。  
  
3.  检查您的应用程序中引用的所有程序集的时间戳。  
  
4.  如果所有被引用的程序集的时间戳晚于您的应用程序的最后一次编译的时间戳，则您的应用程序已过期。  如果发生这种情况，请使用最新的程序集重新编译您的应用程序，并且进行所有必要的代码更改。  
  
5.  重新运行应用程序，执行再现问题的步骤并确认没有出现异常。  
  
## 示例  
 下面的程序通过降低方法的可访问性，并在不重新编译的情况下尝试从其他程序集访问该方法来演示此问题。  首先尝试编译 `changeaccess.cpp`。  它是将发生更改的被引用的程序集。  然后编译 `referencing.cpp`。  编译成功。  现在，降低被调用的方法的可访问性。  使用 `/DCHANGE_ACCESS` 标志重新编译 `changeaccess.cpp`。  这使方法成为受保护方法而不是私有方法，所以能在更大范围内合法调用它。  在不重新编译 `referencing.exe` 的情况下，重新运行应用程序。  将导致异常 <xref:System.MethodAccessException>。  
  
```  
// changeaccess.cpp  
// compile with: /clr:safe /LD  
// After the initial compilation, add /DCHANGE_ACCESS and rerun  
// referencing.exe to introduce an error at runtime. To correct  
// the problem, recompile referencing.exe  
  
public ref class Test {  
#if defined(CHANGE_ACCESS)  
protected:  
#else  
public:  
#endif  
  
  int access_me() {  
    return 0;  
  }  
  
};  
  
```  
  
```  
// referencing.cpp  
// compile with: /clr:safe   
#using <changeaccess.dll>  
  
// Force the function to be inline, to override the compiler's own  
// algorithm.  
__forceinline  
int CallMethod(Test^ t) {  
  // The call is allowed only if access_me is declared public  
  return t->access_me();  
}  
  
int main() {  
  Test^ t = gcnew Test();  
  try  
  {  
    CallMethod(t);  
    System::Console::WriteLine("No exception.");  
  }  
  catch (System::Exception ^ e)  
  {  
    System::Console::WriteLine("Exception!");  
  }  
  return 0;  
}  
  
```  
  
## 请参阅  
 [\#using 指令](../preprocessor/hash-using-directive-cpp.md)   
 [托管类型](../dotnet/managed-types-cpp-cli.md)
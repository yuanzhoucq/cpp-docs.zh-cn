---
title: 如何： 诊断和修复程序集兼容性问题 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4440ab455aff8922c108cdb35cff041cd67f56d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-diagnose-and-fix-assembly-compatibility-problems-ccli"></a>如何：诊断和修复程序集兼容性问题 (C++/CLI)
本主题介绍在编译时引用程序集的版本不匹配在运行时，引用的程序集的版本时可能发生以及如何避免此问题。  
  
 程序集编译时，可能使用引用其他程序集`#using`语法。 在编译期间，由编译器访问这些程序集。 从这些程序集的信息用于优化决策。  
  
 但是，如果引用的程序集是更改而重新编译，并且不重新编译依赖于它的引用程序集，这些程序集可能不是兼容。 已在上均有效的优化决策首先可能不正确与新的程序集版本。 由于这些不兼容性可能会发生各种运行时错误。 没有在这种情况下不会产生任何特定异常。 在运行时报告失败的方式取决于导致问题的代码更改的性质。  
  
 只要会为你的产品的发布版本重新生成整个应用程序，这些错误不应为最终的生产代码中的问题。 公开发布的程序集应带有正式版本号，这将确保避免这些问题。 有关详细信息，请参阅[程序集版本控制](/dotnet/framework/app-domains/assembly-versioning)。  
  
### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>诊断和解决不兼容性错误  
  
1.  如果您遇到运行时异常或引用另一个程序集的代码中出现其他错误情况并且没有其他标识的原因，你可能要处理的过期的程序集。  
  
2.  首先，隔离并重现异常或其他错误条件。 由于过时异常发生的问题，应可重现。  
  
3.  检查在你的应用程序中引用任何程序集的时间戳。  
  
4.  如果任何引用程序集的时间戳晚于应用程序的最后一个编译的时间戳，你的应用程序已过期。 如果发生这种情况，重新编译你的应用程序与最新程序集，并进行所需的任何代码更改。  
  
5.  重新运行应用程序中，执行的步骤，再现该问题，并验证异常不会发生。  
  
## <a name="example"></a>示例  
 以下程序演示了该问题，减少的方法的可访问性，尝试访问无需重新编译中另一个程序集的方法。 请尝试编译`changeaccess.cpp`第一个。 这是所引用的程序集，这将更改。 然后编译`referencing.cpp`。 编译成功。 现在，减少所调用的方法的可访问性。 重新编译`changeaccess.cpp`标志`/DCHANGE_ACCESS`。 因此，可以调用它，再从法律上讲，这使得了受保护，而不是私有的方法。 无需重新编译`referencing.exe`，重新运行应用程序。 异常<xref:System.MethodAccessException>将导致。  
  
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
  
## <a name="see-also"></a>请参阅  
 [#using 指令](../preprocessor/hash-using-directive-cpp.md)   
 [托管类型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)
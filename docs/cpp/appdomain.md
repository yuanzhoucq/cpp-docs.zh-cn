---
title: "appdomain | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "appdomain_cpp"
  - "appdomain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], appdomain"
  - "appdomain __declspec 关键字"
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# appdomain
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定托管应用程序的每个应用程序域应具有其自己的特定全局变量或静态成员变量的副本。  有关更多信息，请参见[应用程序域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)。  
  
 每个应用程序域具有其自己的 per\-appdomain 变量的副本。  在将程序集加载到应用程序域中时执行 appdomain 变量的构造函数，并在卸载应用程序域时执行析构函数。  
  
 如果希望公共语言运行时中进程内的所有应用程序域共享全局变量，请使用 `__declspec(process)` 修饰符。  默认情况下，`__declspec(process)` 在 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 下方生效，并且 `__declspec(appdomain)` 在 **\/clr:pure** 下方生效。  在 **\/clr:safe** 下强制执行 `__declspec(appdomain)`。  
  
 `__declspec(appdomain)` 仅在使用 **\/clr** 编译器选项之一时有效。  只有全局变量、静态成员变量或静态局部变量可以使用 `__declspec(appdomain)` 进行标记。  将 `__declspec(appdomain)` 应用于托管类型的静态成员是错误的，因为它们始终具有此行为。  
  
 使用 `__declspec(appdomain)` 与使用[线程本地存储 \(TLS\)](../parallel/thread-local-storage-tls.md) 类似。  线程具有其自己的存储，就像应用程序域一样。  使用 `__declspec(appdomain)` 可确保全局变量在为此应用程序创建的每个应用程序域中都具有其自己的存储。  
  
 在将 per process 和 per appdomain 变量结合使用方面存在一些限制；有关详细信息，请参阅 [process](../cpp/process.md)。  
  
 例如，在程序启动时，初始化所有 per\-process 变量，然后初始化所有 per\-appdomain 变量。  因此，当初始化 per\-process 变量时，它不能依赖于任何 per\-application 域变量的值。  混合使用（分配）per appdomain 和 per process 变量的做法不妥。  
  
 有关如何在特定应用程序域中调用函数的信息，请参阅 [call\_in\_appdomain 函数](../dotnet/call-in-appdomain-function.md)。  
  
## 示例  
  
```  
// declspec_appdomain.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
class CGlobal {  
public:  
   CGlobal(bool bProcess) {  
      Counter = 10;  
      m_bProcess = bProcess;  
      Console::WriteLine("__declspec({0}) CGlobal::CGlobal constructor", m_bProcess ? (String^)"process" : (String^)"appdomain");  
   }  
  
   ~CGlobal() {  
      Console::WriteLine("__declspec({0}) CGlobal::~CGlobal destructor", m_bProcess ? (String^)"process" : (String^)"appdomain");  
   }  
  
   int Counter;  
  
private:  
   bool m_bProcess;  
};  
  
__declspec(process) CGlobal process_global = CGlobal(true);  
__declspec(appdomain) CGlobal appdomain_global = CGlobal(false);  
  
value class Functions {  
public:  
   static void change() {  
      ++appdomain_global.Counter;  
   }  
  
   static void display() {  
      Console::WriteLine("process_global value in appdomain '{0}': {1}",   
         AppDomain::CurrentDomain->FriendlyName,  
         process_global.Counter);  
  
      Console::WriteLine("appdomain_global value in appdomain '{0}': {1}",   
         AppDomain::CurrentDomain->FriendlyName,  
         appdomain_global.Counter);  
   }  
};  
  
int main() {  
   AppDomain^ defaultDomain = AppDomain::CurrentDomain;  
   AppDomain^ domain = AppDomain::CreateDomain("Domain 1");  
   AppDomain^ domain2 = AppDomain::CreateDomain("Domain 2");  
   CrossAppDomainDelegate^ changeDelegate = gcnew CrossAppDomainDelegate(&Functions::change);  
   CrossAppDomainDelegate^ displayDelegate = gcnew CrossAppDomainDelegate(&Functions::display);  
  
   // Print the initial values of appdomain_global in all appdomains.  
   Console::WriteLine("Initial value");  
   defaultDomain->DoCallBack(displayDelegate);  
   domain->DoCallBack(displayDelegate);  
   domain2->DoCallBack(displayDelegate);  
  
   // Changing the value of appdomain_global in the domain and domain2  
   // appdomain_global value in "default" appdomain remain unchanged  
   process_global.Counter = 20;  
   domain->DoCallBack(changeDelegate);  
   domain2->DoCallBack(changeDelegate);  
   domain2->DoCallBack(changeDelegate);  
  
   // Print values again  
   Console::WriteLine("Changed value");  
   defaultDomain->DoCallBack(displayDelegate);  
   domain->DoCallBack(displayDelegate);  
   domain2->DoCallBack(displayDelegate);  
  
   AppDomain::Unload(domain);  
   AppDomain::Unload(domain2);  
}  
```  
  
  **\_\_declspec\(process\) CGlobal::CGlobal constructor**  
**\_\_declspec\(appdomain\) CGlobal::CGlobal constructor**  
**初始值**  
**process\_global value in appdomain 'declspec\_appdomain.exe': 10**  
**appdomain\_global value in appdomain 'declspec\_appdomain.exe': 10**  
**\_\_declspec\(appdomain\) CGlobal::CGlobal constructor**  
**process\_global value in appdomain 'Domain 1': 10**  
**appdomain\_global value in appdomain 'Domain 1': 10**  
**\_\_declspec\(appdomain\) CGlobal::CGlobal constructor**  
**process\_global value in appdomain 'Domain 2': 10**  
**appdomain\_global value in appdomain 'Domain 2': 10**  
**Changed value**  
**process\_global value in appdomain 'declspec\_appdomain.exe': 20**  
**appdomain\_global value in appdomain 'declspec\_appdomain.exe': 10**  
**process\_global value in appdomain 'Domain 1': 20**  
**appdomain\_global value in appdomain 'Domain 1': 11**  
**process\_global value in appdomain 'Domain 2': 20**  
**appdomain\_global value in appdomain 'Domain 2': 12**  
**\_\_declspec\(appdomain\) CGlobal::~CGlobal destructor**  
**\_\_declspec\(appdomain\) CGlobal::~CGlobal destructor**  
**\_\_declspec\(appdomain\) CGlobal::~CGlobal destructor**  
**\_\_declspec\(process\) CGlobal::~CGlobal destructor**   
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)
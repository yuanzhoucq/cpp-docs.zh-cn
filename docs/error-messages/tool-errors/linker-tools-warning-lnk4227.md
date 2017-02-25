---
title: "链接器工具警告 LNK4227 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4227"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4227"
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 链接器工具警告 LNK4227
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

元数据操作警告 \(HRESULT\) : warning\_message  
  
 链接器在合并时检测出元数据差异：  
  
-   含当前正生成的程序集的一个或多个引用的程序集。  
  
-   编译中的一个或多个源代码文件。  
  
 例如，如果具有两个同名的全局函数，但是声明的参数信息不同（声明在所有 compiland 中都不一致），则可能导致 LNK4227。  在各个 .obj 文件上使用 ildasm.exe \/TEXT \/METADATA `object_file`，您应该看到类型的不一致性。  
  
 LNK4227 还报告由其他工具引发的问题。  例如 al.exe，请参见 [Al.exe 工具错误和警告](http://msdn.microsoft.com/zh-cn/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)。  
  
 必须修复元数据问题才能解决此警告。  
  
 例如，在对引用的程序集进行签名时（不同于引用它的程序集），将生成 LNK4227。  
  
 下面的示例生成 LNK4227：  
  
```  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 然后，  
  
```  
// LNK4227b.cpp  
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
// Try the following line instead  
// [assembly:AssemblyDelaySignAttribute(false)];  
  
ref class MyClass  
{  
};  
```  
  
 下面的示例生成 LNK4227：  
  
```  
// LNK4227c.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 然后，  
  
```  
// LNK4227d.cpp  
// compile with: /clr:oldSyntax LNK4227c.cpp /FeLNK4227d.exe  
#using <mscorlib.dll>  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
  
__gc class MyClass  
{  
};  
```  
  
 版本号以错误格式传递给程序集特性时，也可能生成 LNK4227。“\*”表示法是特定于 AssemblyVersionAttribute 的。若要消除此警告，请仅使用版本特性（除 AssemblyVersionAttribute 之外）中的数字。  
  
 下面的示例生成 LNK4227：  
  
```  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```
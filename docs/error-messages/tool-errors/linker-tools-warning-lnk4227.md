---
title: "链接器工具警告 LNK4227 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ee566318c7d19159f9a2c084d348b5010a65e2de
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-warning-lnk4227"></a>链接器工具警告 LNK4227
元数据操作警告 (HRESULT): warning_message  
  
合并时，链接器检测到元数据之间的差异︰  
  
-   一个或多个引用的程序集与当前正在生成的程序集。  
  
-   一个或多个源代码文件编译中。  
  
例如，可能只有两个具有相同名称但不同声明的参数信息的全局函数引起 LNK4227 （声明并非在所有 compiland 中保持一致）。 使用 ildasm.exe /TEXT /METADATA`object_file`上每个.obj 文件，您应会看到类型有何不同。  
  
LNK4227 还报告由其他工具的问题。 例如，al.exe;请参阅[Al.exe 工具错误和警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)。  
  
若要解决此警告，必须修复的元数据问题。  
  
例如，如果引用的程序集进行签名以不同的方式比引用它的程序集，将生成 LNK4227。  
  
下面的示例生成 LNK4227:  
  
```  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 然后  
  
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
  
在格式不正确的版本号传递给程序集属性时，还会生成 LNK4227。  * 表示法是特定于与 AssemblyVersionAttribute。  若要解决此警告，只能使用数字 AssemblyVersionAttribute 以外的版本属性中。  
  
下面的示例生成 LNK4227:  
  
```  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```

---
title: "链接器工具警告 LNK4227 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4227
dev_langs: C++
helpviewer_keywords: LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c603110d77b06fac59a725ba448f058bd4ad7a38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4227"></a>链接器工具警告 LNK4227  
  
> 元数据操作警告 (*HRESULT*): *warning_message*  
  
在合并时，链接器检测到元数据差异：  
  
-   一个或多个引用的程序集与当前正在生成程序集。  
  
-   一个或多个源代码文件编译中。  
  
如果你有两个具有相同名称但不同声明的参数信息的全局函数例如，可能导致 LNK4227 （即，声明不是在所有编译单位中保持一致）。 使用 ildasm.exe 使用 /TEXT /METADATA *object_file*上每个.obj 文件，以查看类型有何不同。  
  
LNK4227 还可用于源自另一种工具的报告问题。 搜索警告消息以了解更多信息。  
  
若要解决此警告，必须修复元数据问题。  
  
## <a name="example"></a>示例  
  
引用的程序集上不同于引用它的程序集签名时，将生成 LNK4227。  
  
下面的示例生成 LNK4227:  
  
```cpp  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 然后  
  
```cpp  
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
  
## <a name="example"></a>示例  
  
版本号的格式错误传递给程序集特性，则还可以生成 LNK4227。  * 表示法是特定于`AssemblyVersionAttribute`。  若要解决此警告，使用仅统计中的行版本特性而不是`AssemblyVersionAttribute`。  
  
下面的示例生成 LNK4227:  
  
```cpp  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```
---
title: 如何： 检索 Windows 版本 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
ms.assetid: 7e6f567b-d378-49bb-aa59-2240f69a022d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf602bd9fbd0765c54f9955fbb2cfcc3588e96dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33128262"
---
# <a name="how-to-retrieve-the-windows-version-ccli"></a>如何：检索 Windows 版本 (C++/CLI)
下面的代码示例演示如何检索当前操作系统的平台和版本信息。 此信息存储在<xref:System.Environment.OSVersion%2A?displayProperty=fullName>属性组成从广义上讲描述的 Windows 版本的枚举和<xref:System.Environment.Version%2A>对象，其中包含实际版本的操作系统。  
  
## <a name="example"></a>示例  
  
```  
// os_ver.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   OperatingSystem^ osv = Environment::OSVersion;  
   PlatformID id = osv->Platform;  
   Console::Write("Operating system: ");  
  
   if (id == PlatformID::Win32NT)  
      Console::WriteLine("Win32NT");  
   else if (id == PlatformID::Win32S)  
      Console::WriteLine("Win32S");  
   else if (id == PlatformID::Win32Windows)  
      Console::WriteLine("Win32Windows");  
   else  
      Console::WriteLine("WinCE");  
  
   Version^ version = osv->Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write("OS Version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
                   build, major, minor, revision);  
   }  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [Windows 操作 (C + + /cli CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
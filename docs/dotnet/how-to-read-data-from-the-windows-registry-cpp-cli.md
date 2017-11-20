---
title: "如何： 从 Windows 注册表中读取数据 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++, reading from Windows Registry
- registry, reading
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25ab4b9cdba5a9a71d1258960e4da89d2d5e657d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-read-data-from-the-windows-registry-ccli"></a>如何：从 Windows 注册表中读取数据 (C++/CLI)
下面的代码示例使用<xref:Microsoft.Win32.Registry.CurrentUser>键以从 Windows 注册表中读取数据。 首先，使用枚举子项<xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A>使用打开方法，然后标识子项<xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A>方法。 与根键中，每个子项都由<xref:Microsoft.Win32.RegistryKey>类。 最后，使用新<xref:Microsoft.Win32.RegistryKey>对象用于枚举的键/值对。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
## <a name="remarks"></a>备注  
 <xref:Microsoft.Win32.Registry>类是只是静态的实例的容器<xref:Microsoft.Win32.RegistryKey>。 每个实例表示的根注册表节点。 两个实例<xref:Microsoft.Win32.Registry.ClassesRoot>， <xref:Microsoft.Win32.Registry.CurrentConfig>， <xref:Microsoft.Win32.Registry.CurrentUser>， <xref:Microsoft.Win32.Registry.LocalMachine>，和<xref:Microsoft.Win32.Registry.Users>。  
  
 除了为静态中的对象<xref:Microsoft.Win32.Registry>类是只读的。 此外，实例的<xref:Microsoft.Win32.RegistryKey>类创建的用于访问注册表的内容对象也是只读的。 有关如何重写此行为的示例，请参阅[如何： 将数据写入到 Windows 注册表 (C + + /cli CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)。  
  
 有两个其他对象<xref:Microsoft.Win32.Registry>类：<xref:Microsoft.Win32.Registry.DynData>和<xref:Microsoft.Win32.Registry.PerformanceData>。 都的实例<xref:Microsoft.Win32.RegistryKey>类。 <xref:Microsoft.Win32.Registry.DynData>对象包含动态注册表信息，仅支持在 Windows 98 和 Windows me。 <xref:Microsoft.Win32.Registry.PerformanceData>对象可用来访问使用 Windows 性能监视系统的应用程序的性能计数器信息。 <xref:Microsoft.Win32.Registry.PerformanceData>节点表示不实际存储在注册表中，因此不能使用 Regedit.exe 的信息。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 将数据写入到 Windows 注册表 (C + + /cli CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Windows 操作 (C + + /cli CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
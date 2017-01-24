---
title: "如何：从 Windows 注册表中读取数据 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "注册表, 读取"
  - "Visual C++, 从 Windows 注册表中读取"
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：从 Windows 注册表中读取数据 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例使用 <xref:Microsoft.Win32.Registry.CurrentUser> 项从 Windows 注册表中读取数据。  首先，使用 <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> 方法枚举子项，然后使用 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> 方法打开标识子项。  与根项一样，每个子项由 <xref:Microsoft.Win32.RegistryKey> 类来表示。  最后，使用新的 <xref:Microsoft.Win32.RegistryKey> 对象来枚举项\/值对。  
  
## 示例  
  
### 代码  
  
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
  
## 备注  
 <xref:Microsoft.Win32.Registry> 类仅仅是 <xref:Microsoft.Win32.RegistryKey> 的静态实例的一个容器。  每个实例表示一个根注册表节点。  这些实例为 <xref:Microsoft.Win32.Registry.ClassesRoot>、<xref:Microsoft.Win32.Registry.CurrentConfig>、<xref:Microsoft.Win32.Registry.CurrentUser>、<xref:Microsoft.Win32.Registry.LocalMachine> 和 <xref:Microsoft.Win32.Registry.Users>。  
  
 除了为静态实例之外，<xref:Microsoft.Win32.Registry> 类中的对象为只读对象。  而且，为了访问注册表对象的内容而创建的 <xref:Microsoft.Win32.RegistryKey> 类的实例也是只读实例。  有关如何重写此行为的示例，请参见 [如何：将数据写入 Windows 注册表](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)。  
  
 <xref:Microsoft.Win32.Registry> 类中有两个附加对象：<xref:Microsoft.Win32.Registry.DynData> 和 <xref:Microsoft.Win32.Registry.PerformanceData>。  这两个对象都是 <xref:Microsoft.Win32.RegistryKey> 类的实例。  <xref:Microsoft.Win32.Registry.DynData> 对象包含动态注册表信息，这些信息仅在 Windows 98 和 Windows Me 中受支持。  <xref:Microsoft.Win32.Registry.PerformanceData> 对象可用于访问使用 Windows 性能监视系统的应用程序的性能计数器信息。  <xref:Microsoft.Win32.Registry.PerformanceData> 节点表示的信息实际上并不存储于注册表中，因此不能使用 Regedit.exe 进行查看。  
  
## 请参阅  
 [如何：将数据写入 Windows 注册表](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Windows 操作](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
---
title: "如何：将数据写入 Windows 注册表 (C++/CLI) | Microsoft Docs"
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
  - "注册表, 写入"
  - "Visual C++, 写入到 Windows 注册表"
ms.assetid: 3d40b978-4baa-4779-bfe3-47e2917b757f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将数据写入 Windows 注册表 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例使用 <xref:Microsoft.Win32.Registry.CurrentUser> 项创建一个对应于 **Software** 项的 <xref:Microsoft.Win32.RegistryKey> 类的可写实例。  然后使用 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> 方法创建一个新项并将其添加到项\/值对中。  
  
## 示例  
  
### 代码  
  
```  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
## 备注  
 可以使用 .NET Framework 通过 <xref:Microsoft.Win32.Registry> 和 [RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx) 类访问注册表，这两个类都在 <xref:Microsoft.Win32> 命名空间中定义。  **Registry** 类是 <xref:Microsoft.Win32.RegistryKey> 类的静态实例的容器。  每个实例表示一个根注册表节点。  这些实例为 <xref:Microsoft.Win32.Registry.ClassesRoot>、<xref:Microsoft.Win32.Registry.CurrentConfig>、<xref:Microsoft.Win32.Registry.CurrentUser>、<xref:Microsoft.Win32.Registry.LocalMachine> 和 <xref:Microsoft.Win32.Registry.Users>。  
  
## 请参阅  
 [如何：从 Windows 注册表中读取数据](../dotnet/how-to-read-data-from-the-windows-registry-cpp-cli.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
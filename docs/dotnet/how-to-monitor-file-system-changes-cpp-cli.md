---
title: "如何：监视文件系统更改 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "事件 [C++], 监视"
  - "示例 [C++], 监视文件系统更改"
  - "文件系统事件 [C++]"
  - "FileSystemWatcher 类, 示例"
  - "监视文件系统事件"
ms.assetid: 207a3069-e63d-417e-8b56-00ab44f29c52
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：监视文件系统更改 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例使用 <xref:System.IO.FileSystemWatcher> 注册对应于正在创建、更改、删除或重命名的文件的事件。  无需通过定期轮询目录来查看文件更改情况，而可以使用 <xref:System.IO.FileSystemWatcher> 类在检测到更改时激发事件。  
  
## 示例  
  
```  
// monitor_fs.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::IO;  
  
ref class FSEventHandler  
{  
public:  
    void OnChanged (Object^ source, FileSystemEventArgs^ e)  
    {  
        Console::WriteLine("File: {0} {1}",   
               e->FullPath, e->ChangeType);  
    }  
    void OnRenamed(Object^ source, RenamedEventArgs^ e)  
    {  
        Console::WriteLine("File: {0} renamed to {1}",   
                e->OldFullPath, e->FullPath);  
    }  
};  
  
int main()  
{  
   array<String^>^ args = Environment::GetCommandLineArgs();  
  
   if(args->Length < 2)  
   {  
      Console::WriteLine("Usage: Watcher.exe <directory>");  
      return -1;  
   }  
  
   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );  
   fsWatcher->Path = args[1];  
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>   
              (NotifyFilters::FileName |   
               NotifyFilters::Attributes |   
               NotifyFilters::LastAccess |   
               NotifyFilters::LastWrite |   
               NotifyFilters::Security |   
               NotifyFilters::Size );  
  
    FSEventHandler^ handler = gcnew FSEventHandler();   
    fsWatcher->Changed += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Created += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Deleted += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Renamed += gcnew RenamedEventHandler(   
            handler, &FSEventHandler::OnRenamed);  
  
    fsWatcher->EnableRaisingEvents = true;  
  
    Console::WriteLine("Press Enter to quit the sample.");  
    Console::ReadLine( );  
}  
```  
  
## 请参阅  
 [System.IO 命名空间](https://msdn.microsoft.com/en-us/library/system.io.aspx)   
 [文件和流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
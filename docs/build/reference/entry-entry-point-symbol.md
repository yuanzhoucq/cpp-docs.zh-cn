---
title: "/ENTRY（入口点符号） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/entry"
  - "VC.Project.VCLinkerTool.EntryPointSymbol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ENTRY 链接器选项"
  - "ENTRY 链接器选项"
  - "-ENTRY 链接器选项"
  - "起始地址"
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ENTRY（入口点符号）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ENTRY:function  
```  
  
## 备注  
 其中：  
  
 *Function — 函数*  
 一个函数，指定 .exe 文件或 DLL 的用户定义起始地址。  
  
## 备注  
 \/ENTRY 选项将某个入口点函数指定为 .exe 文件或 DLL 的起始地址。  
  
 必须用 `__stdcall` 调用约定来定义函数。  参数和返回值取决于程序是控制台应用程序、 windows 应用程序还是 DLL。  建议让链接器设置入口点，以便 C 运行库正确初始化，并执行静态对象的 C\+\+ 构造函数。  
  
 默认情况下，起始地址为 C 运行库中的函数名。  链接器根据程序的特性来选择该函数，如下表所示。  
  
|函数名|...的默认值|  
|---------|-------------|  
|**mainCRTStartup**（或 **wmainCRTStartup**）|使用 \/SUBSYSTEM:**CONSOLE** 的应用程序；调用 **main**（或 **wmain**）|  
|**WinMainCRTStartup**（或 **wWinMainCRTStartup**）|使用 \/SUBSYSTEM:**WINDOWS** 的应用程序；调用 `WinMain`（或 **wWinMain**），它必须用 `__stdcall` 来定义|  
|**\_DllMainCRTStartup**|一个 DLL；调用 `DllMain`（如果存在，必须用 `__stdcall` 来定义）|  
  
 如果未指定 [\/DLL](../../build/reference/dll-build-a-dll.md) 或 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 选项，则链接器将根据是否定义了 **main** 或 `WinMain` 来选择子系统和入口点。  
  
 函数 **main**、`WinMain` 和 `DllMain` 是三种用户定义的入口点形式。  
  
 在创建托管映像时，使用 \/ENTRY 指定的函数必须具有 \(LPVOID *var1*, DWORD *var2*, LPVOID *var3*\) 的签名。  
  
 有关如何定义自己的 DllMain 入口点的更多信息，请参见[运行库行为](../../build/run-time-library-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改“入口点”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
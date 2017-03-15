---
title: "/DELAYLOAD（延迟加载导入） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/delayload"
  - "VC.Project.VCLinkerTool.DelayLoadDLLS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYLOAD 链接器选项"
  - "DLL 的延迟加载, /DELAYLOAD 选项"
  - "DELAYLOAD 链接器选项"
  - "-DELAYLOAD 链接器选项"
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /DELAYLOAD（延迟加载导入）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DELAYLOAD:dllname  
  
```  
  
## 参数  
 `dllname`  
 想要延迟加载的 DLL 的名称。  
  
## 备注  
 \/DELAYLOAD 选项导致 `dllname` 指定的 DLL 只能在程序第一次调用该 DLL 中的函数时加载。  有关详细信息，请参阅 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)。  你可以根据需要多次使用此选项，以便指定已选的多个 DLL。  当链接你的程序时，你必须使用 Delayimp.lib，或者也可以实现你自己的延迟加载 Helper 函数。  
  
 [\/DELAY](../../build/reference/delay-delay-load-import-settings.md) 选项为每个延迟加载的 DLL 指定绑定和加载选项。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”对话框。  有关详细信息，请参阅 [使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在“链接器”文件夹中，选择“输入”属性页。  
  
3.  修改“延迟加载的 DLL”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
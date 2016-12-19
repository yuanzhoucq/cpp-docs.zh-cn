---
title: "/ALLOWBIND（禁止 DLL 绑定） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.PreventDLLBinding"
  - "/allowbind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWBIND 链接器选项"
  - "ALLOWBIND 链接器选项"
  - "-ALLOWBIND 链接器选项"
  - "绑定 DLL"
  - "DLL [C++], 禁止绑定"
  - "防止 DLL 绑定"
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ALLOWBIND（禁止 DLL 绑定）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ALLOWBIND[:NO]  
```  
  
## 备注  
 \/ALLOWBIND:NO 在 DLL 的标头中设置一个位，向 Bind.exe 指示不允许绑定图像。  如果 DLL 已经进行数字签名（绑定使签名无效），可能不需要绑定 DLL。  
  
 可以使用 EDITBIN 实用工具的 [\/ALLOWBIND](../../build/reference/allowbind.md) 选项编辑 \/ALLOWBIND 功能的现有 DLL。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  依次展开**“配置属性”**、**“链接器”**，然后选择**“命令行”**。  
  
3.  将 `/ALLOWBIND:NO` 输入到**“附加选项”**中。  
  
### 以编程方式设置此链接器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [BindImage 函数](http://msdn.microsoft.com/library/windows/desktop/ms679278.aspx)   
 [BindImageEx 函数](http://msdn.microsoft.com/library/windows/desktop/ms679279.aspx)
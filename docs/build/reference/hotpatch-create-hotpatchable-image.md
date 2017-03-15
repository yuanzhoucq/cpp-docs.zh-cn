---
title: "/hotpatch（创建可热修补的映像） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/hotpatch"
  - "VC.Project.VCCLCompilerTool.CreateHotpatchableImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "热修补"
  - "-hotpatch 编译器选项 [C++]"
  - "/hotpatch 编译器选项 [C++]"
  - "hotpatching"
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# /hotpatch（创建可热修补的映像）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

准备要热修补的映像。  
  
## 语法  
  
```  
/hotpatch  
```  
  
## 备注  
 当 **\/hotpatch** 用于编译时，编译器确保每个函数的第一个指令为至少两个字节，这是热修补的要求。  
  
 若要完成使图像的准备，创建可热修补，在使用 **\/hotpatch** 生成后，必须使用 [\/FUNCTIONPADMIN（创建可热修补的映像）](../../build/reference/functionpadmin-create-hotpatchable-image.md) 链接。  使用一个 cl.exe 的调用来编译和链接映像时，**\/hotpatch** 隐含表示 **\/functionpadmin**。  
  
 由于指令总是两个字节或ARM架构更大，因为x64的编译总是视为**\/hotpatch**已指定，当你编译这三个目标不必指定**\/hotpatch**，但是，你仍然使用**\/functionpadmin**，创建可热修补的映像并将其链接。  **\/hotpatch** 编译器选项仅影响 x86 生成。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  在**“附加选项”**框中添加编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 指导  
 有关以下内容的详细信息更新管理，请参见“更新托管安全指南”[http:\/\/www.microsoft.com\/technet\/security\/guidance\/PatchManagement.mspx](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx)。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
---
title: "/FUNCTIONPADMIN（创建可热修补的映像） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/functionpadmin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FUNCTIONPADMIN 链接器选项"
  - "-FUNCTIONPADMIN 链接器选项"
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /FUNCTIONPADMIN（创建可热修补的映像）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

准备映像进行热修补。  
  
## 语法  
  
```  
/FUNCTIONPADMIN[:space]  
```  
  
## 备注  
 其中，  
  
 `space`（可选）  
 添加到各个函数开头的填充数量，为 5，6 或 16。x86 映像要求填充五个字节、x64映像要求为 6 个字节并且Itanium 处理器家族 \(IPF\) 生成的图像在每个函数开头需要16个字节填充。  
  
 默认情况下，编译器根据映像的计算机类型将正确的空格数添加到映像中。  
  
 为了使链接器生成可热修补的映像，.obj 文件必须已使用 [\/hotpatch（创建可热修补的映像）](../../build/reference/hotpatch-create-hotpatchable-image.md) 进行编译。  
  
 使用 cl.exe 的单个调用来编译和链接映像时，**\/hotpatch** 隐含表示 **\/functionpadmin**。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
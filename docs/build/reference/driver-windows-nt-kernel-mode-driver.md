---
title: "/DRIVER（Windows NT 内核模式驱动程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.driver"
  - "/driver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DRIVER 链接器选项"
  - "DRIVER 链接器选项"
  - "-DRIVER 链接器选项"
  - "内核模式驱动程序"
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /DRIVER（Windows NT 内核模式驱动程序）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DRIVER[:UPONLY | :WDM]  
```  
  
## 备注  
 使用 \/DRIVER 链接器选项可生成 Windows NT 内核模式驱动程序。  
  
 **\/DRIVER:UPONLY** 使链接器将 **IMAGE\_FILE\_UP\_SYSTEM\_ONLY** 位添加到输出头的特性中，以指定它是单处理器 \(UP\) 驱动程序。  操作系统将拒绝在多处理器\(MP\)系统上加载 UP 驱动程序。  
  
 **\/DRIVER:WDM** 使链接器设置可选头的 DllCharacteristics 字段中的 **IMAGE\_DLLCHARACTERISTICS\_WDM\_DRIVER** 位。  
  
 如果未指定 **\/DRIVER**，则链接器不会设置这些位。  
  
 如果指定了 **\/DRIVER**：  
  
-   \/FIXED:NO 有效 \([\/FIXED（固定基址）](../../build/reference/fixed-fixed-base-address.md)\)。  
  
-   输出文件的扩展名将为 .sys。  使用 **\/OUT** 更改默认文件名和扩展名 \([\/OUT（输出文件名）](../../build/reference/out-output-file-name.md)\)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“系统”**属性页。  
  
4.  修改**“驱动程序”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见`P:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.driver`。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
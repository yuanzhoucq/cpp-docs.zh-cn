---
title: "在设计时设置控件属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 属性"
ms.assetid: 963bf498-d371-4cfd-8bed-865427dcfad9
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在设计时设置控件属性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在设计时可以使用对话框编辑器来设置控件的属性。  设置属性时，资源编辑器用指定的值初始化控件。  仍可以编程方式更改属性。  
  
 存在于所有[数据绑定控件](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)中的 **DataSource** 属性使您可以指定要绑定到的[数据源](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)控件。  
  
 当将简单绑定的 ADO 数据绑定控件绑定到 ADO 数据控件 \(ADODC\) 时，必须将 **DataField** 属性设置为行集合中的一个有效字段，以使该控件与某一列关联。  否则，已编译的应用程序将在运行的调试版本中断言（该断言只是注明控件已绑定到空列）。  
  
> [!NOTE]
>  “常规”属性选项卡使您能够指定 .rc 文件所需的控件标识符及其他属性。（.rc 文件在以后编译以生成 Windows 程序资源代码。）  
  
### 在“所有”选项卡中设置属性  
  
1.  [插入 ActiveX 控件](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)到对话框中。  
  
2.  在对话框编辑器中右击该控件，然后单击**“属性”**。  
  
3.  单击**“所有”**选项卡显示该控件的属性。  对于给定属性，输入初始化值。  
  
 若要在运行时设置控件属性，请参见[修改控件的运行时行为](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)。  
  
## 请参阅  
 [使用 ActiveX 控件](../../data/ado-rdo/using-activex-controls.md)
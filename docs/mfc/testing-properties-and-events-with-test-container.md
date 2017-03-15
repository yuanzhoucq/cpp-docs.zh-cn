---
title: "使用测试容器测试属性和事件 | Microsoft Docs"
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
  - "ActiveX 控件测试容器"
  - "ActiveX 控件 [C++], 测试"
  - "调试 ActiveX 控件"
  - "属性 [MFC], 测试"
  - "测试容器"
  - "测试, 测试容器"
  - "tstcon32.exe"
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 使用测试容器测试属性和事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试容器应用程序，提供在 Visual C\+\+ 中，为测试和调试的 ActiveX 控件的 ActiveX 控件容器。  测试容器允许控件可以通过更改其属性，调用方法和激发其事件测试控件的功能。  测试容器可以查看数据并通知绑定记录。测试 ActiveX 控件的持久性功能提供功能：您可以将属性设置为，substorage 到流或重载以及检查存储的流数据。  本节描述如何使用测试容器的基本功能。  对于附加信息，选择 **帮助** 菜单，当运行时测试容器。  
  
### 访问 ActiveX 控件测试容器  
  
1.  创建[TSTCON Sample: ActiveX Control Test Container](../top/visual-cpp-samples.md)。  
  
### 测试ActiveX 控件  
  
1.  在测试容器的**编辑** 菜单上，单击 **Insert New Control**。  
  
2.  在 **Insert New Control** 框中，选择控件并单击 **确定**。  控件将出现在控件容器。  
  
    > [!NOTE]
    >  如果控件在 **插入控件** 对话框没有列出，则确保您已注册它与测试容器 **文件** 菜单上的 **Register Controls** 命令。  
  
 此时可以测试控件的属性或事件。  
  
#### 测试属性  
  
1.  从**Control**菜单中单击**“Invoke Methods”（调用方法）**。  
  
2.  在 **方法名称** 下拉列表中，选择您要测试的属性的 PropPut 方法。  
  
3.  修改 **参数值** 或 **参数类型** 并单击 **设置数值** 按钮。  
  
4.  单击 **调用** 将新值传递给对象。  
  
     如果属性包含新值  
  
#### 测试事件和事件指定信息的目标。  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  指定事件信息的目标。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [如何：调试 ActiveX 控件](../Topic/How%20to:%20Debug%20an%20ActiveX%20Control.md)
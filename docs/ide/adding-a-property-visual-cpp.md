---
title: "添加属性 (Visual C++) | Microsoft Docs"
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
  - "接口, 添加属性"
  - "属性 [C++], 添加到接口"
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 添加属性 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用[添加属性向导](../ide/names-add-property-wizard.md)向项目中的接口添加属性。  
  
### 向对象添加属性  
  
1.  在[类视图](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，右击要向其添加属性的接口名称。  
  
    > [!NOTE]
    >  也可以向调度接口添加属性，调度接口嵌套在库节点中（除非项目已特性化）。  
  
2.  从快捷菜单中单击“添加”，然后单击**“添加属性”**。  
  
3.  在[添加属性向导](../ide/names-add-property-wizard.md)中，提供创建属性的信息。  
  
4.  在该向导的 [IDL 特性](../ide/idl-attributes-add-property-wizard.md)页中，为属性指定所有接口定义语言 \(IDL\) 设置。  
  
5.  单击“完成”添加属性。  
  
 属性的 **Get** 和 `Put` 方法在“类视图”中显示为两个图标，位于定义该属性的接口下。  可以双击其中任一图标查看 .idl 文件中的属性声明。  
  
-   对于 ATL 接口，**Get** 和 **Put** 函数被添加到 .cpp 文件中，对这些函数的引用则添加到 .h 文件中。  
  
-   对于 MFC 调度接口，如果选择“成员变量”作为实现类型，则将一个方法和一个变量添加到实现该接口的类中。  如果选择“Get\/Set 方法”作为实现类型，则将两个方法添加到实现该接口的类中。  
  
## 请参阅  
 [创建 COM 接口](../ide/creating-a-com-interface-visual-cpp.md)   
 [编辑 COM 接口](../ide/editing-a-com-interface.md)   
 [组件对象模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)   
 [接口指针和接口](http://msdn.microsoft.com/library/windows/desktop/ms688484)
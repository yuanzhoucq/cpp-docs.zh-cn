---
title: 添加属性 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00b19fa7166e6edad05d729c5a738a2a827086ae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212790"
---
# <a name="adding-a-property-visual-c"></a>添加属性 (Visual C++)
可以使用[添加属性向导](../ide/names-add-property-wizard.md)，向项目中的接口添加方法。  
  
### <a name="to-add-a-property-to-your-object"></a>向对象添加属性  
  
1.  在[类视图](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中单击要向其添加属性的接口的名称。  
  
    > [!NOTE]
    >  也可以将属性添加到调度接口，它嵌套在库节点中（除非该项目已特性化）。  
  
2.  从快捷菜单中，单击“添加”，然后单击“添加属性”。  
  
3.  在[添加属性向导](../ide/names-add-property-wizard.md)中，提供创建属性的信息。  
  
4.  在向导的 [IDL 特性](../ide/idl-attributes-add-property-wizard.md)页中，为此属性指定任何接口定义语言 (IDL) 设置。  
  
5.  单击“完成”以添加属性。  
  
 属性的 Get 和 `Put` 方法在定义该属性的接口下在类视图中显示为两个图标。 可以双击其中任一图标，查看 .idl 文件中的属性声明。  
  
-   对于 ATL 接口，Get 和 Put 函数已添加到 .cpp 文件，并且对这些函数的引用也添加到 .h 文件。  
  
-   对于 MFC 调度接口，如果选择“成员变量”作为实现类型，则方法和变量将添加到实现它的类中。 如果选择 Get/Set 方法作为实现类型，则两个方法将添加到实现它的类中。  
  
## <a name="see-also"></a>请参阅  
 [创建 COM 接口](../ide/creating-a-com-interface-visual-cpp.md)   
 [编辑 COM 接口](../ide/editing-a-com-interface.md)   
 [组件对象模型](/windows/desktop/com/the-component-object-model)   
 [接口指针和接口](/windows/desktop/com/interface-pointers-and-interfaces)
---
title: "修改控件的运行时行为 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 运行时行为"
ms.assetid: 78b44b0f-0d5a-4da0-8aa2-595f5789c634
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 修改控件的运行时行为
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[插入控件](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)并生成一个或多个[包装类](../../data/ado-rdo/wrapper-classes.md)后，即可调用该控件的方法并编写该控件的事件处理程序。  
  
 控件的[包装类](../../data/ado-rdo/wrapper-classes.md)指定可用于修改该控件运行时行为的函数。 包含适当的包装类头文件并使用这些方法。 若要设置属性，请查找属性名具有 Set 前缀的访问器方法。 若要检索属性，请查找属性名具有 Get 前缀的访问器方法。 可稍后编写事件处理程序。  
  
 由于这些控件是使用自动化来实现的，所以传递的类型只能是可用于自动化的类型（如 BSTR 和 VARIANT）。 虽然可以使用系统调用来分配和设置 BSTR 和 VARIANT，但也许需要使用 ATL 包装类（[CComBSTR](../../atl/reference/ccombstr-class.md)、[CComVariant](../../atl/reference/ccomvariant-class.md)）、Visual C\+\+ COM 编译器支持的包装类（[\_bstr\_t](../../cpp/bstr-t-class.md)、[\_variant\_t](../../cpp/variant-t-class.md)）或 MFC 包装类（[COleVariant](../../mfc/reference/colevariant-class.md)）。  
  
 如果添加数据控件，则插入 ActiveX 控件向导将为该数据控件的组件类（用于管理其内部数据对象）生成包装类。 这些类不包含所有 RDO 或 ADO，而是表示类型库中声明的内部对象。  
  
 如果你想要直接使用 ADO 和 RDO，则应该通过[编译器 COM 支持类](../../cpp/compiler-com-support-classes.md)（它支持 [\#import 指令](../../preprocessor/preprocessor-directives.md)）或通过各自的 SDK 直接连接到 ADO 或 RDO Dll（Msado15.dll 或 Msrdo20.dll）。  
  
## 在运行时设置控件属性  
 请注意，ActiveX 控件的某些属性在运行时可能是只读的，这使动态创建变得困难。 可以通过重写控件容器的 [OnAmbientPropertyChange](../Topic/COleControl::OnAmbientPropertyChange.md) 处理程序，暂时模拟设计模式以便进行属性初始化，如知识库文章“如何：在运行时设置 ActiveX 控件的设计时属性 \(Q260744\)”中所述。 可在 [http:\/\/support.microsoft.com\/](http://support.microsoft.com/) 上查找知识库文章。  
  
## 请参阅  
 [使用 ActiveX 控件](../../data/ado-rdo/using-activex-controls.md)
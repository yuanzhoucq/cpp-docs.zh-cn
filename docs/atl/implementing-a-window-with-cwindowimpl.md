---
title: "Implementing a Window with CWindowImpl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWindowImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 窗口"
  - "subclassing ATL window classes"
  - "superclassing, ATL"
  - "windows [C++], ATL"
  - "windows [C++], subclassing"
  - "windows [C++], superclassing"
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Implementing a Window with CWindowImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要实现窗口中，从 `CWindowImpl`派生选件类。  在派生类中，声明消息映射和消息处理函数。  您可以通过三种不同的方法现在可以使用您的选件类:  
  
-   [创建基于新的Windows选件类的窗口](#_atl_creating_a_window_based_on_a_new_windows_class)  
  
-   [创建超类时现有Windows选件类](#_atl_superclassing_an_existing_windows_class)  
  
-   [子类现有的窗口](#_atl_subclassing_an_existing_window)  
  
##  <a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> 创建基于新的Windows选件类的窗口  
 `CWindowImpl` 包含 [DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md) 宏声明Windows选件类信息。  此宏实现 `GetWndClassInfo` 功能，使用 [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 定义新的Windows选件类的信息。  当 `CWindowImpl::Create` 调用时，此Windows选件类中，并且新的窗口中创建。  
  
> [!NOTE]
>  `CWindowImpl` 通过 **NULL** 到 `DECLARE_WND_CLASS` 宏，这意味着ATL将生成一个Windows类名。  若要指定自己的名称，请传递字符串对 `CWindowImpl`的 `DECLARE_WND_CLASS` 派生类。  
  
## 示例  
 以下实现基于新的Windows选件类的窗口选件类的示例:  
  
 [!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/CPP/implementing-a-window-with-cwindowimpl_1.h)]  
  
 若要创建窗口中，将创建 `CMyWindow` 实例然后调用 **Create** 方法。  
  
> [!NOTE]
>  若要重写默认Windows选件类信息，请通过设置 `CWndClassInfo` 成员执行在派生类中 `GetWndClassInfo` 方法为适当的值。  
  
##  <a name="_atl_superclassing_an_existing_windows_class"></a> 创建超类现有Windows选件类  
 [DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md) 宏允许您创建承载的窗口创建现有Windows选件类。  指定此宏在您的 `CWindowImpl`派生类。  与其他ATL窗口中，消息由消息映射处理。  
  
 当您使用 `DECLARE_WND_SUPERCLASS`，新的Windows选件类将注册。  此新选件类将与现有选件类使用 `CWindowImpl::WindowProc` 指定，但是，替换窗口过程的相同\(或重写此方法\)的功能。  
  
## 示例  
 下面的选件该类的示例显示标准的编辑选件类的创建:  
  
 [!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/CPP/implementing-a-window-with-cwindowimpl_2.h)]  
  
 若要创建要为其创建超类的编辑窗口中，创建 `CMyEdit` 实例然后调用 **Create** 方法。  
  
##  <a name="_atl_subclassing_an_existing_window"></a> Subclassing现有的窗口  
 对子类现有的窗口，从 `CWindowImpl` 派生选件类并声明消息映射，在前两个大小写。  然而，请注意，您未指定任何Windows选件类信息，因为您将子类一个现有窗口。  
  
 而不是调用 **Create**，请调用 `SubclassWindow` 并将该句柄所需的子类的现有窗口。  在窗口子类，它将使用 `CWindowImpl::WindowProc` \(或重写此方法\)的功能处理消息传送到消息映射。  取消从对象中的一个子类窗口，请调用 `UnsubclassWindow`。  然后将还原windows的原始窗口过程。  
  
## 请参阅  
 [Implementing a Window](../atl/implementing-a-window.md)
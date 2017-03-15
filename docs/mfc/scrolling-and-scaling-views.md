---
title: "滚动和缩放视图 | Microsoft Docs"
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
  - "消息处理程序"
  - "消息处理, 视图类中的滚动条"
  - "缩放视图"
  - "滚动条, 消息"
  - "滚动视图"
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 滚动和缩放视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 支持 Scroll 自动缩放到框架窗口的大小显示自己的视图和视图。  `CScrollView` 类支持两个视图。  
  
 有关滚动和缩放的更多信息，请参见 [CScrollView](../mfc/reference/cscrollview-class.md) 在 *MFC 参考* 类。  滚动有关示例，请参见 [SCRIBBLE 示例](../top/visual-cpp-samples.md)。  
  
## 您想进一步了解什么？  
  
-   滚动视图  
  
-   缩放视图  
  
-   [\<caps:sentence id\="tgt8" sentenceid\="f321fcf7c88bc6e3f892ae0fc9b2f0d8" class\="tgtSentence"\>坐标视图\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a> 滚动视图  
 频繁文档范围比其大小视图查看大。  这可能发生，因为文档的数据添加或用户配置时视图的窗口。  在此类情况下，视图必须支持 Scroll。  
  
 可以处理所有视图在其 `OnHScroll` 和 `OnVScroll` 成员函数的滚动条消息。  可以实现 Scroll 条消息处理这些函数，完成任何工作，也可以使用 `CScrollView` 类处理。的滚动。  
  
 `CScrollView` 执行以下操作：  
  
-   管理窗口和视区大小和映射模式  
  
-   自动滚动响应滚动条消息  
  
 可以指定多少搜索“页”\(当用户单击中滚动轴时\) 和“行”滚动 \(在用户滚动箭头单击时\)。  计划这些值与视图的性质。  例如，可能需要滚动以图形视图 1 像素的增量，但是会基于在文本文档的行高度的增量。  
  
##  <a name="_core_scaling_a_view"></a> 缩放视图  
 当希望视图自动以适应其框架窗口时的大小，则可以使用缩放使用 `CScrollView` 代替滚动。  逻辑视图拉伸或收缩正确地适合窗口的工作区。  缩放一的视图没有滚动条。  
  
## 请参阅  
 [使用视图](../mfc/using-views.md)
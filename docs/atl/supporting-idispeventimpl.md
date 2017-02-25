---
title: "Supporting IDispEventImpl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, IDispEventImpl support in COM objects"
  - "BEGIN_SINK_MAP macro"
  - "event sink maps, 声明"
  - "IDispEventImpl class, advising and unadvising"
  - "IDispEventImpl class, 声明"
  - "SINK_ENTRY macro"
  - "类型库, 导入"
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Supporting IDispEventImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板选件类 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 来提供支持连接点在您的ATL选件类的接收器。  连接点接收允许从外部COM对象处理事件激发的选件类。  这些连接点接收映射与事件接收器映射，假定由您的选件类。  
  
 正确实现连接点您的选件类的接收器，下面的步骤必须完成:  
  
-   导入每个外部对象的类型库  
  
-   声明 `IDispEventImpl` 接口  
  
-   声明事件接收器映射  
  
-   建议，并且连接点的unadvise  
  
 在实现涉及的步骤连接点接收所有通过修改仅标头文件完成\(.h\)您的选件类。  
  
## 导入类型库  
 为事件要处理，必须导入类型库的每个外部对象。  此步骤定义可以处理的事件并提供时，使用声明事件接收器映射中的信息。  [\#import](../preprocessor/hash-import-directive-cpp.md) 指令可用于完成此操作。  将您将支持到标头文件的每个调度接口所必需的 `#import` 指令行\(.h\)您的选件类。  
  
 下面的示例导入外部COM服务器\(`MSCAL.Calendar.7`\)的类型库:  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/CPP/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  必须有一个外部类型的将支持的库单独的 `#import` 语句。  
  
## 声明IDispEventImpl接口  
 既然已导入每个调度接口的类型库，您需要声明每个外部调度接口的单独 `IDispEventImpl` 接口。  通过将每个外部对象的一个 `IDispEventImpl` 接口声明修改您的选件类的说明。  有关参数的更多信息，请参见 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)。  
  
 下面的代码声明连接点接收的两个示例，`DCalendarEvents` 接口的，因此，为了选件类实现的COM对象 `CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/CPP/supporting-idispeventimpl_2.h)]  
  
## 声明事件接收器映射  
 为了适当的函数中处理的事件通知，您的选件类必须将每个事件为其正确的处理程序。  这是通过声明事件接收器映射实现。  
  
 ATL提供多个宏、 [BEGIN\_SINK\_MAP](../Topic/BEGIN_SINK_MAP.md)、 [END\_SINK\_MAP](../Topic/END_SINK_MAP.md)和 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY.md)，使此映射会更加轻松。  标准格式如下:  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `.  .  .  //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 下面的示例声明一个具有两个事件处理程序的事件接收器映射:  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/CPP/supporting-idispeventimpl_3.h)]  
  
 实现接近完成。  最后一步相关建议和unadvising外部接口。  
  
## 建议和Unadvising IDispEventImpl接口  
 最后一步是将执行建议的方法\(或\) unadvise所有连接点在适当的时间。  必须在外部客户端和您的对象之间的通信之前执行建议的时可能会出现。  在对象变得可见之前，该对象支持的每个外部调度接口为输出接口中查询。  建立连接后，引用与输出接口用于从对象的事件。  此过程称为“建议”。  
  
 在对象完成与外部接口后，应注意输出接口您的选件类不再使用它们。  此过程称为“unadvising”。  
  
 由于COM对象的唯一谓词，此过程有所不同，详细和执行，在实现之间。  这些详细信息超出了本主题讨论范围以外但没有解决。  
  
## 请参阅  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)
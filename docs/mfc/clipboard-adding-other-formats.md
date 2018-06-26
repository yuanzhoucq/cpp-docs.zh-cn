---
title: 剪贴板： 添加其他格式 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67004ac43193d47720626da241a8030ba396abdf
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932012"
---
# <a name="clipboard-adding-other-formats"></a>剪贴板：添加其他格式
本主题说明如何扩展支持的格式，特别是对于 OLE 支持的列表。 主题[剪贴板： 复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)描述了支持从剪贴板复制和粘贴所需的最小实现。 如果这是所有实现，放到剪贴板上的唯一格式会**CF_METAFILEPICT**， **CF_EMBEDSOURCE**， **CF_OBJECTDESCRIPTOR**，并有可能延长**CF_LINKSOURCE**。 大多数应用程序将需要在剪贴板上比这三种的更多格式。  
  
##  <a name="_core_registering_custom_formats"></a> 注册自定义格式  
 若要创建您自己的自定义格式，请按照相同的过程将使用在注册任何自定义剪贴板格式时： 传递到格式的名称**RegisterClipboardFormat**函数，并将其返回值用作格式 id。  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a> 放置在剪贴板上的格式  
 若要将更多格式添加到那些放到剪贴板上，必须重写`OnGetClipboardData`从派生类中的函数`COleClientItem`或`COleServerItem`（具体取决于是否有本机要复制的数据）。 在此函数中，应使用以下过程。  
  
#### <a name="to-place-formats-on-the-clipboard"></a>将格式放置在剪贴板上  
  
1.  创建 `COleDataSource` 对象。  
  
2.  将此数据源传递到的函数，将本机数据格式添加到支持的格式列表中，通过调用`COleDataSource::CacheGlobalData`。  
  
3.  通过调用添加标准格式`COleDataSource::CacheGlobalData`为每个你想要支持的标准格式。  
  
 在 MFC OLE 示例程序中使用此技术[HIERSVR](../visual-cpp-samples.md) (检查`OnGetClipboardData`成员函数**CServerItem**类)。 此示例中的唯一区别是第三步未实现因为 HIERSVR 不支持任何其他标准格式。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [OLE 数据对象和数据源以及统一数据传输](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [OLE 拖放](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>请参阅  
 [剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)


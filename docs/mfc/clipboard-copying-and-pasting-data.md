---
title: "剪贴板：复制和粘贴数据 | Microsoft Docs"
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
  - "剪贴板, 将数据复制到"
  - "剪贴板, 粘贴"
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 剪贴板：复制和粘贴数据
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此主题描述实现复制到和粘贴来自在 OLE 应用程序的剪贴板的必需的最小工作量。  建议您在执行之前读取 [数据对象与数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) 主题。  
  
 在实现复制或粘贴之前，必须先"编辑"菜单上提供函数处理复制，剪切、粘贴和选项。  
  
##  <a name="_core_copying_or_cutting_data"></a> 复制或剪切数据  
  
#### 将数据复制到剪贴板  
  
1.  确定复制的数据是否为本机数据或是嵌套的或链接的项。  
  
    -   如果数据事被嵌入或链接的，请获取一个指向选定的 `COleClientItem` 对象的指针。  
  
    -   如果数据是本地的并且应用程序时一个服务器，则创建一个新的对象从 `COleServerItem` 继承获取选定的数据。  否则，创建数据的一个 `COleDataSource` 对象。  
  
2.  调用选定项的 `CopyToClipboard` 成员函数。  
  
3.  如果用户选择剪切操作而不是复制操作，请删除应用程序选定的数据。  
  
 若要查看此序列的示例，请参阅示例程序 [OCLIENT](../top/visual-cpp-samples.md) 在 MFC OLE 和 [HIERSVR](../top/visual-cpp-samples.md)的 **OnEditCut** 和 **OnEditCopy** 函数。  请注意这些示例维护一个指向当前选择的数据的指针，因此步骤 1 已完成。  
  
##  <a name="_core_pasting_data"></a> 传递数据  
 粘贴数据比复制它更复杂，因为在将需要选择格式传递数据到应用程序。  
  
#### 从剪贴板中粘贴数据。  
  
1.  在视图类中，请实现 **OnEditPaste** 处理选择粘贴选项的用户从"编辑"菜单。  
  
2.  在 **OnEditPaste** 函数中，创建 `COleDataObject` 对象并调用它的 `AttachClipboard` 成员函数连接此对象到剪贴板的数据。  
  
3.  调用 `COleDataObject::IsDataAvailable` 检查特定格式是否可用。  
  
     或者，可以使用 `COleDataObject::BeginEnumFormats` 查找其他格式，直到找到最适合应用程序。  
  
4.  执行格式的粘贴。  
  
 有关如何工作的示例，请参阅在 MFC OLE 示例程序定义的视图类的 **OnEditPaste** 成员函数的实现和 [OCLIENT](../top/visual-cpp-samples.md) [HIERSVR](../top/visual-cpp-samples.md)。  
  
> [!TIP]
>  在自身的函数中分隔粘贴操作的主要好处是可以使用同一粘贴代码，当在拖放操作期间数据被拖放到应用程序。  在 OCLIENT 和 HIERSVR，`OnDrop` 函数也可以调用 **DoPasteItem**，重用代码写入实现粘贴操作。  
  
 若要处理"编辑"菜单的粘贴特殊选择，请参阅主题 [在 OLE 的对话框](../mfc/dialog-boxes-in-ole.md)。  
  
### 您想进一步了解什么？  
  
-   [添加其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [OLE 数据对象与数据源和统一传输数据](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [OLE 拖放](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## 请参阅  
 [剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
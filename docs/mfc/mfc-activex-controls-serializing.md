---
title: MFC ActiveX 控件： 序列化 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74d62411747dbe920b772b66d11cd1e2a789c5db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 控件：序列化
本文讨论如何序列化 ActiveX 控件。 在序列化的读取或写入到持久存储介质，例如磁盘文件的过程。 Microsoft 基础类 (MFC) 库中类进行序列化提供内置支持`CObject`。 `COleControl` 此将支持扩展到通过属性交换机制使用 ActiveX 控件。  
  
 ActiveX 控件的序列化实现通过重写[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)。 此函数在加载过程中调用，并保存的控件对象中，将存储使用成员变量或具有更改通知的成员变量实现的所有属性。  
  
 以下主题介绍与序列化 ActiveX 控件相关的主要问题：  
  
-   实现`DoPropExchange`函数控制对象进行序列化  
  
-   [自定义序列化过程](#_core_customizing_the_default_behavior_of_dopropexchange)  
  
-   [实现版本支持](#_core_implementing_version_support)  
  
##  <a name="_core_implementing_the_dopropexchange_function"></a> DoPropExchange 函数的实现  
 当你使用 ActiveX 控件向导来生成控件项目时，多个默认处理程序函数会自动添加到控件类，包括的默认实现[COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange)。 下面的示例显示添加到类中使用 ActiveX 控件向导创建的代码：  
  
 [!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]  
  
 如果你想要让属性保持不变，修改`DoPropExchange`通过添加对属性 exchange 函数的调用。 下面的示例演示序列化的自定义布尔 CircleShape 属性，其中 CircleShape 属性具有默认值为**TRUE**:  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]  
  
 下表列出可用于序列化控件的属性的可能属性 exchange 函数：  
  
|属性交换函数|目标|  
|---------------------------------|-------------|  
|**PX_Blob （)**|将序列化为二进制大型对象 (BLOB) 数据属性的类型。|  
|**PX_Bool （)**|序列化的类型的布尔属性。|  
|**PX_Color （)**|序列化的类型颜色属性。|  
|**PX_Currency （)**|序列化类型**CY** （货币） 属性。|  
|**PX_Double （)**|序列化类型**double**属性。|  
|**PX_Font （)**|序列化的字体类型属性。|  
|**PX_Float （)**|序列化类型**float**属性。|  
|**PX_IUnknown （)**|序列化类型的属性`LPUNKNOWN`。|  
|**PX_Long （)**|序列化类型**长**属性。|  
|**PX_Picture （)**|序列化类型图片属性。|  
|**PX_Short （)**|序列化类型**短**属性。|  
|**PXstring （)**|序列化类型`CString`属性。|  
|**PX_ULong （)**|序列化类型**ULONG**属性。|  
|**PX_UShort （)**|序列化类型**USHORT**属性。|  
  
 有关这些属性交换函数的详细信息，请参阅[持久性的 OLE 控件](../mfc/reference/persistence-of-ole-controls.md)中*MFC 参考*。  
  
##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> 自定义 DoPropExchange 的默认行为  
 默认实现**DoPropertyExchange** （如前一个主题中所示） 进行调用以基类`COleControl`。 此序列化的自动支持的属性集`COleControl`，这将比序列化仅控件的自定义属性的更多存储空间。 删除此调用允许你只序列化这些属性您认为重要的对象。 对控件已实现任何常用属性状态将不进行序列化当保存或加载控件对象，除非你显式添加**PX_** 调用它们。  
  
##  <a name="_core_implementing_version_support"></a> 实现版本支持  
 版本支持修改后的 ActiveX 控件来添加新的持久性属性，仍将能够检测并加载由该控件的早期版本创建的持久性状态。 若要使控件的版本可作为其持久性数据的一部分，调用[COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion)该控件的`DoPropExchange`函数。 如果 ActiveX 控件使用 ActiveX 控件向导创建，则此调用会自动插入。 如果不需要版本支持，可以删除它。 但是，在控件大小的成本是非常小 （4 字节为单位） 以提供版本支持增加灵活性。  
  
 如果未使用 ActiveX 控件向导创建控件，添加对的调用`COleControl::ExchangeVersion`的方法是插入以下行的开头你`DoPropExchange`函数 (对的调用之前`COleControl::DoPropExchange`):  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 你可以使用任何`DWORD`作为的版本号。 ActiveX 控件向导生成的项目使用 **_wVerMinor**和 **_wVerMajor**作为默认值。 这些是在项目的 ActiveX 控件类的实现文件中定义的全局常量。 中的其余部分你`DoPropExchange`函数，你可以调用[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)在任何时间，以检索要保存或检索的版本。  
  
 在下面的示例中，版本 1 的此示例控件具有只有一个"ReleaseDate"属性。 版本 2 添加了一个"OriginalDate"属性。 如果控件指示从旧版本中加载的持久状态，它将初始化为默认值的新属性的成员变量。  
  
 [!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 默认情况下，控件""旧将数据转换为最新格式。 例如，如果版本 2 的控制加载已保存的版本 1 的数据，它将再次保存时编写的版本 2 格式。 如果你想要将数据保存在格式上次读取的控件，将传递**FALSE**作为第三个参数调用时`ExchangeVersion`。 此第三个参数是可选的它是**TRUE**默认情况下。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)


---
title: "MFC ActiveX 控件：序列化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_wVerMinor"
  - "DoPropExchange"
  - "_wVerMajor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoPropExchange 方法"
  - "ExchangeVersion 方法"
  - "GetVersion 方法"
  - "MFC ActiveX 控件, 序列化"
  - "MFC ActiveX 控件, 版本支持"
  - "版本控制 ActiveX 控件"
  - "wVerMajor 全局常量"
  - "wVerMinor 全局常量"
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：序列化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论如何序列化 ActiveX 控件。  序列化是读取或编写过程到持久性存储媒体，例如磁盘文件。  Microsoft 基础类 \(MFC\) \(MFC\) 库为 `CObject`的类序列化提供内置支持。  `COleControl` 到 ActiveX 控件支持此属性通过使用交换机制。  
  
 ActiveX 控件的序列化重写实现。[COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md) 此函数，在控件调用对象的加载和保存过程中，全部存储属性实现具有一个成员或变量一个成员变量的更改通知。  
  
 以下主题包含关联的主要问题。序列化 ActiveX 控件：  
  
-   实现 `DoPropExchange` 函数序列化控件对象中  
  
-   [自定义序列化过程](#_core_customizing_the_default_behavior_of_dopropexchange)  
  
-   [实现生成支持](#_core_implementing_version_support)  
  
##  <a name="_core_implementing_the_dopropexchange_function"></a> 实现DoPropExchange函数  
 在将 ActiveX 控件向导生成控件项目时，若干默认处理程序函数会自动添加到控件类，包括 [COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)的默认实现。  下面的示例演示代码添加到类。创建 ActiveX 控件向导：  
  
 [!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_1.cpp)]  
  
 如果希望属性不可变，通过添加修改调用 `DoPropExchange` 向属性交换函数。  下面的示例演示自定义布尔 CircleShape 属性的序列化，CircleShape 属性具有默认值：**TRUE**  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_3.cpp)]  
  
 下表列出了可以使用序列化控件的属性的属性交换函数：  
  
|交换函数属性|用途|  
|------------|--------|  
|**PX\_Blob\( \)**|序列化类型的二进制大对象 \(BLOB\) \(BLOB\) 数据属性。|  
|**PX\_Bool\( \)**|序列化布尔值类型属性。|  
|**PX\_Color\( \)**|序列化类型颜色属性。|  
|**PX\_Currency\( \)**|序列化类型 **CY** \(货币\) 属性。|  
|**PX\_Double\( \)**|序列化类型 **double** 的属性。|  
|**PX\_Font\( \)**|序列化字体类型属性。|  
|**PX\_Float\( \)**|序列化类型 **浮动** 的属性。|  
|**PX\_IUnknown\( \)**|序列化 `LPUNKNOWN`类型的属性。|  
|**PX\_Long\( \)**|序列化类型 **long** 的属性。|  
|**PX\_Picture\( \)**|序列化类型图片属性。|  
|**PX\_Short\( \)**|序列化类型 **short** 的属性。|  
|**PX\_String\( \)**|序列化 `CString` 类型的属性。|  
|**PX\_ULong\( \)**|序列化类型 **ULONG** 的属性。|  
|**PX\_UShort\( \)**|序列化类型 **USHORT** 的属性。|  
  
 有关这些属性交换函数的更多信息，请参见" *MFC 参考"中的*[OLE 控件持久性](../mfc/reference/persistence-of-ole-controls.md)。  
  
##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> 自定义 DoPropExchange 默认行为  
 **DoPropertyExchange** 的默认实现 \(如上一代主题中演示\) 调用基类 `COleControl`。  这序列化 `COleControl`自动支持的一组属性，与序列化只有控件的自定义属性使用更多的存储空间。  删除此对象允许调用序列化您视为的那些属性。  任何常用属性指定控件实现了不序列化，当加载或保存控件中对象时，除非显式添加 **PX\_** 调用它们。  
  
##  <a name="_core_implementing_version_support"></a> 实现生成支持  
 版本支持允许经过变动的 ActiveX 控件添加新的元素属性并仍然能够检测和加载控件的早期版本创建的持久性的状态。  使控件的版本可用作为其持久性数据的一部分，在控件调用 [COleControl::ExchangeVersion](../Topic/COleControl::ExchangeVersion.md) 的 `DoPropExchange` 函数。  使用 ActiveX 控件向导，如果 ActiveX 控件创建此调用自动插入。  它，则版本支持不是必需的，可移除。  但是，在控件大小的成本。版本支持提供的灵活性非常少 \(4 字节\)。  
  
 如果控件未使用创建 ActiveX 控件向导，添加一个对 `COleControl::ExchangeVersion` 的调用。通过插入下面的行从 `DoPropExchange` 函数的开头 \(在对 `COleControl::DoPropExchange`的调用之前\):  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_4.cpp)]  
  
 可以使用 `DWORD` 作为所有版本号。  ActiveX 控件向导使用的项目生成 **\_wVerMinor** 和 **\_wVerMajor** 为默认。  这些是项目中的 ActiveX 控件类实现文件定义的全局常数。  在 `DoPropExchange` 函数的其余部分中，可以随时调用 [CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md) 检索所保存或检索的版本。  
  
 在下面的示例中，版本 1 拥有此示例控件只有一个“ReleaseDate”属性。  版本 2 添加了“OriginalDate”属性。  如果控件被标记以前版本加载持久状态，初始化新属性的成员变量为默认值。  
  
 [!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_5.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_4.cpp)]  
  
 默认情况下，控件中“转换”旧数据到最新的格式。  例如，在中，如果控件的 2 版由加载 1 版本保存的数据，将编写生成 2 格式，并在再次保存。  如果希望控件的格式保存数据持续读取，将 **FALSE** 作为第三个参数，则调用 `ExchangeVersion`。  第三个参数是可选的和 **TRUE** 是默认方法。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)
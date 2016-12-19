---
title: "OLE 控件的持久性 | Microsoft Docs"
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
  - "vc.mfc.macros.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE 控件, 持久性"
  - "持久性, OLE 控件"
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
caps.latest.revision: 17
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 控件的持久性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 控件的一功能是属性保持 \(或序列化\)，允许 OLE 控件从一文件或流读取或写入属性值。  甚至在应用程序销毁控件之后，容器应用程序使用序列化存储控件的属性值。  当创建控件的新实例之后， OLE 控件的属性值能从文件或流中读取。  
  
### OLE 控件的持久性  
  
|||  
|-|-|  
|[PX\_Blob](../Topic/PX_Blob.md)|交换存储二进制大对象 \(BLOB\) 数据的控件属性。|  
|[PX\_Bool](../Topic/PX_Bool.md)|交换 **BOOL** 类型的控件属性。|  
|[PX\_Color](../Topic/PX_Color.md)|交换控件的颜色属性。|  
|[PX\_Currency](../Topic/PX_Currency.md)|交换 **CY** 类型的控件属性。|  
|[PX\_DataPath](../Topic/PX_DataPath.md)|交换 `CDataPathProperty` 类型的控件属性。|  
|[PX\_Double](../Topic/PX_Double.md)|交换 **double** 类型的控件属性。|  
|[PX\_Font](../Topic/PX_Font.md)|交换控件的字体属性。|  
|[PX\_Float](../Topic/PX_Float.md)|交换 **float** 类型的控件属性。|  
|[PX\_IUnknown](../Topic/PX_IUnknown.md)|交换未定义类型的控件属性。|  
|[PX\_Long](../Topic/PX_Long.md)|交换 **long** 类型的控件属性。|  
|[PX\_Picture](../Topic/PX_Picture.md)|交换控件的图片属性。|  
|[PX\_Short](../Topic/PX_Short.md)|交换 **short** 类型的控件属性。|  
|[PX\_ULong](../Topic/PX_ULong.md)|交换 **ULONG** 类型的控件属性。|  
|[PX\_UShort](../Topic/PX_UShort.md)|交换 **USHORT** 类型的控件属性。|  
|[PX\_String](../Topic/PX_String.md)|交换一个字符的字符串控件属性。|  
|[PX\_VBXFontConvert](../Topic/PX_VBXFontConvert.md)|交换 VBX 控件的相关字体的属性到 OLE 控件字体属性。|  
  
 此外，提供 `AfxOleTypeMatchGuid` 全局函数来测试 `TYPEDESC` 和特定 GUID 之间的匹配。  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
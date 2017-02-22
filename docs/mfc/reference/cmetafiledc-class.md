---
title: "CMetaFileDC Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMetaFileDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMetaFileDC class"
  - "图元文件, 实现"
  - "Windows metafiles [C++]"
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMetaFileDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现一个Windows图元文件，包含图形设备接口\(GDI\)序列顺序可以重播创建一个所需图像或文本。  
  
## 语法  
  
```  
class CMetaFileDC : public CDC  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMetaFileDC::CMetaFileDC](../Topic/CMetaFileDC::CMetaFileDC.md)|构造 `CMetaFileDC` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMetaFileDC::Close](../Topic/CMetaFileDC::Close.md)|关闭设备上下文并创建图元文件句柄。|  
|[CMetaFileDC::CloseEnhanced](../Topic/CMetaFileDC::CloseEnhanced.md)|关闭引发图元文件设备上下文并创建引发图元文件句柄。|  
|[CMetaFileDC::Create](../Topic/CMetaFileDC::Create.md)|创建Windows图元文件设备上下文并将它附加到 `CMetaFileDC` 对象。|  
|[CMetaFileDC::CreateEnhanced](../Topic/CMetaFileDC::CreateEnhanced.md)|创建引发格式图元文件中的图元文件设备上下文。|  
  
## 备注  
 若要实现Windows图元文件，请首先创建一 `CMetaFileDC` 对象。  调用 `CMetaFileDC` 构造函数，然后调用 [创建](../Topic/CMetaFileDC::Create.md) 成员函数，创建Windows图元文件设备上下文并将它附加到 `CMetaFileDC` 对象。  
  
 接下来请发送 `CDC` GDI顺序排序的 `CMetaFileDC` 对象为它预期播放。  创建输出，例如 `MoveTo` 和 `LineTo`可以使用的那些GDI命令。  
  
 在发送用户输入命令。该图元文件后，调用 **Close** 成员函数，关闭图元文件设备上下文并返回图元文件句柄。  然后处理 `CMetaFileDC` 对象。  
  
 [CDC::PlayMetaFile](../Topic/CDC::PlayMetaFile.md) 可以使用图元文件句柄重复播放该图元文件。  图元文件可以由Windows函数来操作\(例如 [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480)，将一个图元文件到磁盘。  
  
 当该图元文件不再需要时，与 [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) Windows函数的内存删除它。  
  
 您还可以实现 `CMetaFileDC` 对象，以便可以处理输出调用，并且属性GDI调用例如 `GetTextExtent`。  此类图元文件更为灵活，并且可以更轻松地重新使用泛型GDI代码，通常包括输出的组合，并且名为的属性。  `CMetaFileDC` 选件类继承两个设备上下文，`m_hDC` 和 `m_hAttribDC`，从 `CDC`。  所有 [CDC](../../mfc/reference/cdc-class.md) GDI输出调用的 `m_hDC` 设备上下文句柄，以及所有 `CDC` GDI属性调用的 `m_hAttribDC` 设备上下文句柄。  通常，这两个设备上下文引用同一计算机。  默认情况下在 `CMetaFileDC`，属性DC设置为 **NULL**。  
  
 除了图元文件之外，创建指向屏幕、打印机或设备的第二个设备上下文，然后调用 `SetAttribDC` 成员函数将新的设备上下文与 `m_hAttribDC`。  GDI要求信息现在将定向到新的 `m_hAttribDC`。  输出GDI调用将转到 `m_hDC`，表示该图元文件。  
  
 有关 `CMetaFileDC`的更多信息，请参见 [设备上下文](../../mfc/device-contexts.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)
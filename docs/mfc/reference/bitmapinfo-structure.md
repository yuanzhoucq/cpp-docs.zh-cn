---
title: "BITMAPINFO 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BITMAPINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BITMAPINFO 结构"
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# BITMAPINFO 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

该 `BITMAPINFO` 的结构定义的尺寸和颜色信息的Windows设备无关位图（DIB）。  
  
## 语法  
  
```  
typedef struct tagBITMAPINFO {  
   BITMAPINFOHEADER bmiHeader;  
   RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### 参数  
 `bmiHeader`  
 指定 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) 的结构，它包含有关尺寸和设备无关位图的颜色格式信息。  
  
 `bmiColors`  
 指定 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) 或 `DWORD` 定义位图中的颜色数据类型。  
  
## 备注  
 设备无关位图由两个不同的部分：一个 `BITMAPINFO` 的结构，描述了位图的尺寸和颜色，并指定位图像素的字节数组。  数组中的位在一起，但每个扫描行必须以零填充结束一个 `LONG` 边界。  如果该高度为正数的，位图的原点为左下角。  如果该高度为负，原点是该左上角。  
  
 一个 *包位图* 是一个位图，其中的字节数组紧跟在 `BITMAPINFO` 结构。  打包的位图由一个指针引用。  
  
 有关 `BITMAPINFO` 结构和对 `BITMAPINFOHEADER` 和 `RGBQUAD` 结构的成员适当的值的详细信息，请参阅 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 文档。  
  
-   [\<caps:sentence id\="tgt11" sentenceid\="b5dd2e8c9cedbac12eb858bd01a029a2" class\="tgtSentence"\>BITMAPINFO 结构\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
-   [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) 结构  
  
-   [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) 结构  
  
## 要求  
 **Header:** wingdi.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)
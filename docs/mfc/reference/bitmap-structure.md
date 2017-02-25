---
title: "BITMAP 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BITMAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BITMAP 结构"
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# BITMAP 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**BITMAP**结构定义了一个逻辑位图**.**的高度、宽度、颜色格式和位值  
  
## 语法  
  
```  
  
      typedef struct tagBITMAP {  /* bm */  
   int bmType;  
   int bmWidth;  
   int bmHeight;  
   int bmWidthBytes;  
   BYTE bmPlanes;  
   BYTE bmBitsPixel;  
   LPVOID bmBits;  
} BITMAP;  
```  
  
#### 参数  
 "bm型"  
 指定位图类型。  逻辑位图，此成员必须为 0。  
  
 "bm宽度"  
 以像素为单位指定位图的宽度。  此宽度必须大于 0。  
  
 “bm高度”  
 光栅行指定位图的高度。  此高度必须大于 0。  
  
 “bm宽字节”  
 在每光栅行指定字节数。  此值必须是偶数，因为图形设备接口 \(GDI\) 假定位图的位值窗体整数 \(2 字节\) 值。  换言之，**bmWidthBytes**\* 8 必须是16 下一个倍数，大于或等于获取的值，当**bmWidth**成员乘以 **bmBitsPixel** 成员时。  
  
 "bm平面"  
 在位图指定颜色产生的数目。  
  
 "bm位像素"  
 在每个需要定义像素的平面指定相邻颜色的位数。  
  
 "bm位"  
 指向位图位值的位置。   **bmBits** 成员必须是1字节数组的长指针。  
  
## 备注  
 当前使用的位图格式是纯色和颜色。  单色位图，使用 1 位 1 平面格式。  每个扫描是 16 位的倍数。  
  
 按如下方式为单色位图 *n*高度扫描：  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 单色设备的像素是黑色或白色。  如果位图中对应的位是 1 ，像素打开\(白色\)。  如果位图中对应的位是 0 ，像素关闭\(黑色\)。  
  
 在 [CDC::GetDeviceCaps](../Topic/CDC::GetDeviceCaps.md)成员函数的**RASTERCAPS**索引中，所有设备支持具有**RC\_BITBLT** bit设置的位图。  
  
 每个设备具有自己的唯一颜色格式。  为了从一个设备调用位图到另一个设备，请使用[GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879) 和 [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) Windows 函数。  
  
## 要求  
 "头部：" wingdi.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap::CreateBitmapIndirect](../Topic/CBitmap::CreateBitmapIndirect.md)
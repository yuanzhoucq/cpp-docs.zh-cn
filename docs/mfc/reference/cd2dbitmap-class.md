---
title: "CD2DBitmap 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DBitmap"
  - "CD2DBitmap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DBitmap 类"
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DBitmap 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Bitmap 的包装。  
  
## 语法  
  
```  
class CD2DBitmap : public CD2DResource;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmap::CD2DBitmap](../Topic/CD2DBitmap::CD2DBitmap.md)|已重载。  从 HBITMAP 构造 CD2DBitmap 对象。|  
|[CD2DBitmap::~CD2DBitmap](../Topic/CD2DBitmap::~CD2DBitmap.md)|该析构函数。  当 D2D 位图对象被销毁时调用。|  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmap::CD2DBitmap](../Topic/CD2DBitmap::CD2DBitmap.md)|已重载。  构造 CD2DBitmap 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmap::Attach](../Topic/CD2DBitmap::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DBitmap::CopyFromBitmap](../Topic/CD2DBitmap::CopyFromBitmap.md)|将指定的区域从指定的位图复制到当前位图|  
|[CD2DBitmap::CopyFromMemory](../Topic/CD2DBitmap::CopyFromMemory.md)|将指定的区域从内存复制到当前位图|  
|[CD2DBitmap::CopyFromRenderTarget](../Topic/CD2DBitmap::CopyFromRenderTarget.md)|将指定的区域从指定的呈现器目标复制到当前位图|  
|[CD2DBitmap::Create](../Topic/CD2DBitmap::Create.md)|创建 CD2DBitmap。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DBitmap::Destroy](../Topic/CD2DBitmap::Destroy.md)|销毁 CD2DBitmap 对象。  （重写 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)。）|  
|[CD2DBitmap::Detach](../Topic/CD2DBitmap::Detach.md)|将资源接口从该对象分离|  
|[CD2DBitmap::Get](../Topic/CD2DBitmap::Get.md)|返回 ID2D1Bitmap 接口|  
|[CD2DBitmap::GetDPI](../Topic/CD2DBitmap::GetDPI.md)|返回位图每英寸点数 \(DPI\)|  
|[CD2DBitmap::GetPixelFormat](../Topic/CD2DBitmap::GetPixelFormat.md)|检索该位图的像素格式和 alpha 模式|  
|[CD2DBitmap::GetPixelSize](../Topic/CD2DBitmap::GetPixelSize.md)|返回该位图的大小，以与设备相关的单位（像素）表示|  
|[CD2DBitmap::GetSize](../Topic/CD2DBitmap::GetSize.md)|返回该位图的大小，以与设备无关的像素 \(DIP\) 为单位|  
|[CD2DBitmap::IsValid](../Topic/CD2DBitmap::IsValid.md)|检查资源有效性（重写 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)。）|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmap::CommonInit](../Topic/CD2DBitmap::CommonInit.md)|初始化对象|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmap::operator ID2D1Bitmap\*](../Topic/CD2DBitmap::operator%20ID2D1Bitmap*.md)|返回 ID2D1Bitmap 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmap::m\_bAutoDestroyHBMP](../Topic/CD2DBitmap::m_bAutoDestroyHBMP.md)|如果要销毁 m\_hBmpSrc，则为 TRUE；否则为 FALSE。|  
|[CD2DBitmap::m\_hBmpSrc](../Topic/CD2DBitmap::m_hBmpSrc.md)|源位图句柄。|  
|[CD2DBitmap::m\_lpszType](../Topic/CD2DBitmap::m_lpszType.md)|资源类型。|  
|[CD2DBitmap::m\_pBitmap](../Topic/CD2DBitmap::m_pBitmap.md)|存储指向 ID2D1Bitmap 对象的指针。|  
|[CD2DBitmap::m\_sizeDest](../Topic/CD2DBitmap::m_sizeDest.md)|位图目标大小。|  
|[CD2DBitmap::m\_strPath](../Topic/CD2DBitmap::m_strPath.md)|位图文件路径。|  
|[CD2DBitmap::m\_uiResID](../Topic/CD2DBitmap::m_uiResID.md)|位图资源 ID。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBitmap](../../mfc/reference/cd2dbitmap-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)
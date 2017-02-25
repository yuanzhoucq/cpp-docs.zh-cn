---
title: "CD2DBitmapBrush 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DBitmapBrush"
  - "afxrendertarget/CD2DBitmapBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DBitmapBrush 类"
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DBitmapBrush 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1BitmapBrush 的包装。  
  
## 语法  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](../Topic/CD2DBitmapBrush::CD2DBitmapBrush.md)|已重载。  从文件构造 CD2DBitmapBrush 对象。|  
|[CD2DBitmapBrush::~CD2DBitmapBrush](../Topic/CD2DBitmapBrush::~CD2DBitmapBrush.md)|该析构函数。  当 D2D 位图画笔对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmapBrush::Attach](../Topic/CD2DBitmapBrush::Attach.md)|将现有的资源接口附加到该对象|  
|[CD2DBitmapBrush::Create](../Topic/CD2DBitmapBrush::Create.md)|创建 CD2DBitmapBrush。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DBitmapBrush::Destroy](../Topic/CD2DBitmapBrush::Destroy.md)|销毁 CD2DBitmapBrush 对象。  （重写 [CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md)。）|  
|[CD2DBitmapBrush::Detach](../Topic/CD2DBitmapBrush::Detach.md)|将资源接口从该对象分离|  
|[CD2DBitmapBrush::Get](../Topic/CD2DBitmapBrush::Get.md)|返回 ID2D1BitmapBrush 接口|  
|[CD2DBitmapBrush::GetBitmap](../Topic/CD2DBitmapBrush::GetBitmap.md)|获取此画笔用来绘制的位图源|  
|[CD2DBitmapBrush::GetExtendModeX](../Topic/CD2DBitmapBrush::GetExtendModeX.md)|获取画笔用来水平平铺那些超出其位图的区域的方法|  
|[CD2DBitmapBrush::GetExtendModeY](../Topic/CD2DBitmapBrush::GetExtendModeY.md)|获取画笔用来垂直平铺那些超出其位图的区域的方法|  
|[CD2DBitmapBrush::GetInterpolationMode](../Topic/CD2DBitmapBrush::GetInterpolationMode.md)|获取该画笔位图在进行缩放或旋转时使用的内插方法|  
|[CD2DBitmapBrush::SetBitmap](../Topic/CD2DBitmapBrush::SetBitmap.md)|指定此画笔用来绘制的位图源|  
|[CD2DBitmapBrush::SetExtendModeX](../Topic/CD2DBitmapBrush::SetExtendModeX.md)|指定画笔如何水平平铺那些超出其位图的区域|  
|[CD2DBitmapBrush::SetExtendModeY](../Topic/CD2DBitmapBrush::SetExtendModeY.md)|指定画笔如何垂直平铺那些超出其位图的区域|  
|[CD2DBitmapBrush::SetInterpolationMode](../Topic/CD2DBitmapBrush::SetInterpolationMode.md)|指定该画笔位图在进行缩放或旋转时使用的内插模式|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmapBrush::CommonInit](../Topic/CD2DBitmapBrush::CommonInit.md)|初始化对象|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmapBrush::operator ID2D1BitmapBrush\*](../Topic/CD2DBitmapBrush::operator%20ID2D1BitmapBrush*.md)|返回 ID2D1BitmapBrush 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DBitmapBrush::m\_pBitmap](../Topic/CD2DBitmapBrush::m_pBitmap.md)|存储指向 CD2DBitmap 对象的指针。|  
|[CD2DBitmapBrush::m\_pBitmapBrush](../Topic/CD2DBitmapBrush::m_pBitmapBrush.md)|存储指向 ID2D1BitmapBrush 对象的指针。|  
|[CD2DBitmapBrush::m\_pBitmapBrushProperties](../Topic/CD2DBitmapBrush::m_pBitmapBrushProperties.md)|位图画笔属性。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DBitmapBrush](../../mfc/reference/cd2dbitmapbrush-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)
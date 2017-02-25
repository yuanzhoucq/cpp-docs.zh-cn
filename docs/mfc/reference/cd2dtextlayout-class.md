---
title: "CD2DTextLayout 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DTextLayout"
  - "afxrendertarget/CD2DTextLayout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DTextLayout 类"
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# CD2DTextLayout 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

IDWriteTextLayout 的包装。  
  
## 语法  
  
```  
class CD2DTextLayout : public CD2DResource;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DTextLayout::CD2DTextLayout](../Topic/CD2DTextLayout::CD2DTextLayout.md)|构造 CD2DTextLayout 对象。|  
|[CD2DTextLayout::~CD2DTextLayout](../Topic/CD2DTextLayout::~CD2DTextLayout.md)|该析构函数。  当 D2D 文本层对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DTextLayout::Create](../Topic/CD2DTextLayout::Create.md)|创建 CD2DTextLayout。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DTextLayout::Destroy](../Topic/CD2DTextLayout::Destroy.md)|销毁 CD2DTextLayout 对象。  （重写 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)。）|  
|[CD2DTextLayout::Get](../Topic/CD2DTextLayout::Get.md)|返回 IDWriteTextLayout 接口|  
|[CD2DTextLayout::GetFontFamilyName](../Topic/CD2DTextLayout::GetFontFamilyName.md)|复制指定位置处的文本的字体系列名称。|  
|[CD2DTextLayout::GetLocaleName](../Topic/CD2DTextLayout::GetLocaleName.md)|获取指定位置处文本的区域设置名称。|  
|[CD2DTextLayout::IsValid](../Topic/CD2DTextLayout::IsValid.md)|检查资源有效性（重写 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)。）|  
|[CD2DTextLayout::ReCreate](../Topic/CD2DTextLayout::ReCreate.md)|重新创建 CD2DTextLayout。  （重写 [CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md)。）|  
|[CD2DTextLayout::SetFontFamilyName](../Topic/CD2DTextLayout::SetFontFamilyName.md)|设置指定文本范围内以 NULL 结尾的文本字体系列名称|  
|[CD2DTextLayout::SetLocaleName](../Topic/CD2DTextLayout::SetLocaleName.md)|设置指定文本范围内的区域设置文本名称|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DTextLayout::operator IDWriteTextLayout\*](../Topic/CD2DTextLayout::operator%20IDWriteTextLayout*.md)|返回 IDWriteTextLayout 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DTextLayout::m\_pTextLayout](../Topic/CD2DTextLayout::m_pTextLayout.md)|指向 IDWriteTextLayout 的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)
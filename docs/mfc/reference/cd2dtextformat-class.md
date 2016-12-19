---
title: "CD2DTextFormat 类 | Microsoft Docs"
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
  - "afxrendertarget/CD2DTextFormat"
  - "CD2DTextFormat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DTextFormat 类"
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DTextFormat 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

IDWriteTextFormat 的包装。  
  
## 语法  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DTextFormat::CD2DTextFormat](../Topic/CD2DTextFormat::CD2DTextFormat.md)|构造 CD2DTextFormat 对象。|  
|[CD2DTextFormat::~CD2DTextFormat](../Topic/CD2DTextFormat::~CD2DTextFormat.md)|该析构函数。  当 D2D 文本格式对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DTextFormat::Create](../Topic/CD2DTextFormat::Create.md)|创建 CD2DTextFormat。  （重写 [CD2DResource::Create](../Topic/CD2DResource::Create.md)。）|  
|[CD2DTextFormat::Destroy](../Topic/CD2DTextFormat::Destroy.md)|销毁 CD2DTextFormat 对象。  （重写 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)。）|  
|[CD2DTextFormat::Get](../Topic/CD2DTextFormat::Get.md)|返回 IDWriteTextFormat 接口|  
|[CD2DTextFormat::GetFontFamilyName](../Topic/CD2DTextFormat::GetFontFamilyName.md)|获取该字体系列名称的副本。|  
|[CD2DTextFormat::GetLocaleName](../Topic/CD2DTextFormat::GetLocaleName.md)|获取该区域设置名称的副本。|  
|[CD2DTextFormat::IsValid](../Topic/CD2DTextFormat::IsValid.md)|检查资源有效性（重写 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)。）|  
|[CD2DTextFormat::ReCreate](../Topic/CD2DTextFormat::ReCreate.md)|重新创建 CD2DTextFormat。  （重写 [CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md)。）|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DTextFormat::operator IDWriteTextFormat\*](../Topic/CD2DTextFormat::operator%20IDWriteTextFormat*.md)|返回 IDWriteTextFormat 接口|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CD2DTextFormat::m\_pTextFormat](../Topic/CD2DTextFormat::m_pTextFormat.md)|指向 IDWriteTextFormat 的指针。|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)
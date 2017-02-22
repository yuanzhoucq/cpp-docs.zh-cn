---
title: "CPictureHolder Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "Picture"
  - "CPictureHolder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控件 [MFC], OLE"
  - "CPictureHolder class"
  - "OLE 控件, 图像"
  - "Picture property"
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CPictureHolder Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现一个图片属性，允许用户显示在控件的图片。  
  
## 语法  
  
```  
class CPictureHolder  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPictureHolder::CPictureHolder](../Topic/CPictureHolder::CPictureHolder.md)|构造 `CPictureHolder` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPictureHolder::CreateEmpty](../Topic/CPictureHolder::CreateEmpty.md)|创建一个空的 `CPictureHolder` 对象。|  
|[CPictureHolder::CreateFromBitmap](../Topic/CPictureHolder::CreateFromBitmap.md)|创建位图的一 `CPictureHolder` 对象。|  
|[CPictureHolder::CreateFromIcon](../Topic/CPictureHolder::CreateFromIcon.md)|创建从图标的一 `CPictureHolder` 对象。|  
|[CPictureHolder::CreateFromMetafile](../Topic/CPictureHolder::CreateFromMetafile.md)|创建从图元文件的一 `CPictureHolder` 对象。|  
|[CPictureHolder::GetDisplayString](../Topic/CPictureHolder::GetDisplayString.md)|检索控件容器的属性浏览器显示的字符串。|  
|[CPictureHolder::GetPictureDispatch](../Topic/CPictureHolder::GetPictureDispatch.md)|返回 `CPictureHolder` 对象的 `IDispatch` 接口。|  
|[CPictureHolder::GetType](../Topic/CPictureHolder::GetType.md)|指示 `CPictureHolder` 对象是否为位图、图元文件或图标。|  
|[CPictureHolder::Render](../Topic/CPictureHolder::Render.md)|呈现图片。|  
|[CPictureHolder::SetPictureDispatch](../Topic/CPictureHolder::SetPictureDispatch.md)|设置 `CPictureHolder` 对象的 `IDispatch` 接口。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPictureHolder::m\_pPict](../Topic/CPictureHolder::m_pPict.md)|到照片对象的指针。|  
  
## 备注  
 `CPictureHolder` 没有基类。  
  
 股票图片属性，开发人员可以用于显示指定位图、图标或图元文件。  
  
 有关创建自定义图片属性的信息，请参见文章 [MFC ActiveX控件:使用在ActiveX控件的图片](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)。  
  
## 继承层次结构  
 `CPictureHolder`  
  
## 要求  
 **Header:** afxctl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFontHolder Class](../../mfc/reference/cfontholder-class.md)
---
title: "CPropExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPropExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控件 [MFC], OLE"
  - "CPropExchange 类"
  - "OLE 控件, 持久性"
ms.assetid: ed872180-e770-4942-892a-92139d501fab
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CPropExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持持久性实现您的OLE控件的。  
  
## 语法  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPropExchange::ExchangeBlobProp](../Topic/CPropExchange::ExchangeBlobProp.md)|交换二进制大对象\(BLOB\)属性。|  
|[CPropExchange::ExchangeFontProp](../Topic/CPropExchange::ExchangeFontProp.md)|交换一个字体属性。|  
|[CPropExchange::ExchangePersistentProp](../Topic/CPropExchange::ExchangePersistentProp.md)|交换控件和文件之间的属性。|  
|[CPropExchange::ExchangeProp](../Topic/CPropExchange::ExchangeProp.md)|交换任何内置类型属性。|  
|[CPropExchange::ExchangeVersion](../Topic/CPropExchange::ExchangeVersion.md)|交换OLE控件的版本号。|  
|[CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md)|检索OLE控件的版本号。|  
|[CPropExchange::IsAsynchronous](../Topic/CPropExchange::IsAsynchronous.md)|确定属性是否完成异步方式交换|  
|[CPropExchange::IsLoading](../Topic/CPropExchange::IsLoading.md)|指示属性是否加载到控件或从它保存。|  
  
## 备注  
 `CPropExchange` 没有基类。  
  
 建立属性交换的上下文和方向。  
  
 持久性是属性，通常表示的状态信息的替换，控件"和"之间。  
  
 框架使用从 `CPropExchange` 派生的对象，当收到通知时OLE控件的属性将填充或存储到持久性存储区。  
  
 框架通过指针传递给了控件的 `DoPropExchange` 函数的这 `CPropExchange` 对象。  如果使用向导创建控件的起始文件，则控件的 `DoPropExchange` 函数调用 `COleControl::DoPropExchange`。  该基类的版本交换控件股票属性;您修改您的派生类的版本交换您添加到控件的属性。  
  
 `CPropExchange` 可用于序列化控件的属性或初始化控件的属性在控件的负载或创建。  `CPropExchange` 的 `ExchangeProp` 和 `ExchangeFontProp` 成员函数可以存储属性设置为并从不同的媒体加载。  
  
 有关使用 `CPropExchange`的更多信息，请参见文章 [MFC ActiveX控件:属性页](../../mfc/mfc-activex-controls-property-pages.md)。  
  
## 继承层次结构  
 `CPropExchange`  
  
## 要求  
 **Header:** afxctl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)
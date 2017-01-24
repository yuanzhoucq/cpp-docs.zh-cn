---
title: "IErrorRecordsImpl 类 | Microsoft Docs"
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
  - "ATL::IErrorRecordsImpl"
  - "ATL.IErrorRecordsImpl"
  - "IErrorRecordsImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IErrorRecordsImpl 类"
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现 OLE DB 接口，[IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 日志添加到并检索记录数据成员 \([m\_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)\) 类型 **CAtlArray\<**`RecordClass`**\>**。  
  
## 语法  
  
```  
template <  
   class T,   
   class RecordClass = ATLERRORINFO  
>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### 参数  
 `T`  
 从 `IErrorRecordsImpl`派生的类。  
  
 `RecordClass`  
 显示 OLE DB 错误对象的类。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|从错误的记录获取错误说明字符串。|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|从错误的记录获取错误 GUID。|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|从错误的记录获取帮助上下文 ID。|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|从错误的记录获取帮助文件的完整路径名。|  
|[GetErrorSource](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|从错误的记录获取错误源代码。|  
  
### 接口方法  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|添加记录到 OLE DB 错误对象。|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|返回有关错误的基本信息，如返回代码并提供程序特定错误号。|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|返回指针对自定义错误对象的接口。|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|返回在中指定的记录的接口指针。[IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx)|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|错误返回参数。|  
|[GetRecordCount](../Topic/CDaoRecordset::GetRecordCount.md)|返回的记录数。OLE DB 记录对象的。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|记录一个错误。|  
  
## 要求  
 **页眉：**atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
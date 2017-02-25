---
title: "CDataSource::OpenWithServiceComponents | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource::OpenWithServiceComponents"
  - "OpenWithServiceComponents"
  - "CDataSource.OpenWithServiceComponents"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenWithServiceComponents 方法"
ms.assetid: 49c1d037-36ae-4fde-8e54-ced623abe1a9
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CDataSource::OpenWithServiceComponents
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 oledb32.dll 中的服务组件打开数据源对象。  
  
## 语法  
  
```  
  
        HRESULT OpenWithServiceComponents (  
   const CLSID clsid,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1   
);  
HRESULT OpenWithServiceComponents (  
   LPCSTR szProgID,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1   
);  
```  
  
#### 参数  
 `clsid`  
 \[in\] 数据提供程序的 **CLSID**。  
  
 `szProgID`  
 \[in\] 数据提供程序的程序 ID。  
  
 `pPropset`  
 \[in\] 指向一个 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构的数组的指针，该结构包含要设置的属性和值。  请参阅 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 中 *OLE DB 程序员参考*中的[属性设置和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)。  如果数据源对象进行初始化，则属性必须属于数据源属性组。  如果同一个属性在 `pPropset` 中多次指定，则使用的值特定于提供程序。  如果 `ulPropSets` 为零，则忽略此参数。  
  
 `ulPropSets`  
 \[in\] 传入 *pPropSet* 参数的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 结构的数目。  如果这是零，则提供程序会忽略 `pPropset`。  
  
## 返回值  
 一个标准 `HRESULT`。  
  
## 备注  
 此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。  有关详细信息，请参阅位于 [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true) 的“OLE DB 程序员参考”中的“OLE DB 服务”。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)
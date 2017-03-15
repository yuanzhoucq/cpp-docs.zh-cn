---
title: "重写动态访问器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "访问器 [C++], dynamic"
  - "动态访问器"
  - "重写, 动态访问器"
ms.assetid: cbefd156-6da5-490d-b795-c2d7d874f7ce
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 重写动态访问器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当使用动态访问器如 `CDynamicAccessor` 时，命令 **Open** 方法将根据已打开的行集合的列信息自动为您创建访问器。  可以重写该动态访问器以精确控制列的绑定方式。  
  
 若要重写动态访问器，请将 **false** 作为最后一个参数传递到 `CCommand::Open` 方法。  这将防止 **Open** 自动创建访问器。  然后可以调用 `GetColumnInfo`，并为要绑定的每一列调用 `AddBindEntry`。  以下代码显示如何执行此操作：  
  
```  
USES_CONVERSION;  
double   dblProductID;  
  
CCommand<CDynamicAccessor> product;  
// Open the table, passing false to prevent automatic binding   
product.Open(session, _T("Select * FROM Products"), NULL, NULL, DBGUID_DEFAULT, false);  
  
ULONG         nColumns;  
DBCOLUMNINFO*   pColumnInfo;  
// Get the column information from the opened rowset.  
product.GetColumnInfo(&nColumns, &pColumnInfo);  
  
// Bind the product ID as a double.  
pColumnInfo[0].wType          = DBTYPE_R8;  
pColumnInfo[0].ulColumnSize = 8;  
product.AddBindEntry(pColumnInfo[0]);  
  
// Bind the product name as it is.  
product.AddBindEntry(pColumnInfo[1]);  
  
// Bind the reorder level as a string.  
pColumnInfo[8].wType          = DBTYPE_STR;  
pColumnInfo[8].ulColumnSize = 10;  
product.AddBindEntry(pColumnInfo[8]);  
  
// You have finished specifying the bindings. Go ahead and bind.  
product.Bind();  
// Free the memory for the column information that was retrieved in   
// previous call to GetColumnInfo.  
CoTaskMemFree(pColumnInfo);  
  
char*   pszProductName;  
char*   pszReorderLevel;  
bool   bRC;  
  
// Loop through the records tracing out the information.  
while (product.MoveNext() == S_OK)  
{  
   bRC = product.GetValue(1, &dblProductID);  
   pszProductName   = (char*)product.GetValue(2);  
   pszReorderLevel  = (char*)product.GetValue(9);  
  
   ATLTRACE(_T("Override = %lf \"%s\" \"%s\"\n"), dblProductID,  
      A2T(pszProductName), A2T(pszReorderLevel));  
}  
```  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)
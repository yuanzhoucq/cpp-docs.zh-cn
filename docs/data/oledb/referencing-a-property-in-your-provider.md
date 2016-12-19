---
title: "在提供程序中引用属性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供程序, 属性"
  - "引用, 提供程序中的属性"
  - "引用提供程序中的属性"
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在提供程序中引用属性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

查找所需属性的属性组和属性 ID。  有关更多信息，请参见“OLE DB Programmer's Reference”（《OLE DB 程序员参考》）中的 [OLE DB 属性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)。  
  
 下面的示例假设您正尝试从行集合中获取属性。  使用会话或命令的代码与此类似，但使用不同的接口。  
  
 创建 [CDBPropSet](../../data/oledb/cdbpropset-class.md) 对象，将属性组用作构造函数的参数。  例如：  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
```  
  
 调用 [AddProperty](../../data/oledb/cdbpropset-addproperty.md)，向它传递属性 ID 和要分配给属性的值。  值的类型取决于正使用的属性。  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_IRowsetChange, true);  
propset.AddProperty(DBPROP_UPDATABILITY,  
DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);  
```  
  
 使用 `IRowset` 接口调用 **GetProperties**。  将属性集作为参数传递。  这是最终的代码：  
  
```  
CAgentRowset<CMyProviderCommand>* pRowset = (CAgentRowset<CMyProviderCommand>*) pThis;  
  
CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;  
  
DBPROPIDSET set;  
set.AddPropertyID(DBPROP_BOOKMARKS);  
DBPROPSET* pPropSet = NULL;  
ULONG ulPropSet = 0;  
HRESULT hr;  
  
if (spRowsetProps)  
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  
if (pPropSet)  
{  
   CComVariant var = pPropSet->rgProperties[0].vValue;  
   CoTaskMemFree(pPropSet->rgProperties);  
   CoTaskMemFree(pPropSet);  
  
   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))  
   {  
      ...  // Use property here  
   }  
}  
```  
  
## 请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)
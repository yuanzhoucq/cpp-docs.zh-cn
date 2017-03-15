---
title: "使用现有 ADO 记录集 | Microsoft Docs"
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
  - "ADO 记录集 [C++]"
  - "OLE DB 使用者模板, ADO 记录集"
  - "记录集 [C++], 在 OLE DB 中使用"
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用现有 ADO 记录集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要将 OLE DB 使用者模板和活动数据对象 \(ADO\) 结合起来，请使用 ADO 打开记录集（此记录集与 OLE DB 使用者模板中的行集合相对应）。  拥有记录集后，执行以下操作以连接到 OLE DB 行集合：  
  
1.  为 `IRowset` 和 `IAccessor` 指针调用 `QueryInterface`。  
  
    ```  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk* 指向 ADO 记录集的 **IUnknown** 对象。  
  
2.  将访问器和行集合附加到适当的 OLE DB 使用者模板类。  
  
    ```  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)
---
title: "获取数据 | Microsoft Docs"
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
  - "数据 [C++], 获取"
  - "获取"
  - "OLE DB 使用者模板 [C++], 获取数据"
  - "行集合 [C++], 获取"
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 获取数据
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

打开数据源、会话和行集合对象后，就可以获取数据了。  根据所使用的访问器类型，可能需要绑定列。  
  
### 获取数据  
  
1.  使用适当的 **Open** 命令打开行集合。  
  
2.  如果使用的是 `CManualAccessor`，则绑定输出列（如果尚未绑定）。  若要绑定这些列，请调用 `GetColumnInfo`，然后用这些绑定创建访问器，如下面的示例所示：  
  
    ```  
    // From the DBViewer Sample CDBTreeView::OnQueryEdit  
    // Get the column information  
    ULONG ulColumns       = 0;  
    DBCOLUMNINFO* pColumnInfo  = NULL;  
    LPOLESTR pStrings      = NULL;  
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)  
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);  
    struct MYBIND* pBind = new MYBIND[ulColumns];  
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);  
    for (ULONG l=0; l<ulColumns; l++)  
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);  
    rs.Bind();  
    ```  
  
3.  编写 `while` 循环以检索数据。  在此循环中，调用 `MoveNext` 以推进游标并根据 S\_OK 测试返回值，如下例所示：  
  
    ```  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
4.  在 `while` 循环内部，可以根据访问器类型获取数据。  
  
    -   如果使用 [CAccessor](../../data/oledb/caccessor-class.md) 类，则应具有一个包含数据成员的用户记录。  可以使用这些数据成员访问数据，如下例所示：  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   如果使用 `CDynamicAccessor` 或 `CDynamicParameterAccessor` 类，可以通过使用访问函数 `GetValue` 和 `GetColumn` 获取数据，如下例所示。  如果想确定所使用的数据类型，请使用 `GetType`。  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the dynamic accessor functions to retrieve your data.  
  
            ULONG ulColumns = rs.GetColumnCount();  
            for (ULONG i=0; i<ulColumns; i++)  
            {  
                rs.GetValue(i);  
            }  
        }  
        ```  
  
    -   如果使用 `CManualAccessor`，则必须指定您自己的数据成员，亲自绑定这些数据成员并直接访问它们，如下例所示：  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## 请参阅  
 [使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)
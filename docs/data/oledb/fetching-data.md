---
title: 提取数据 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab03da7c303552a715c6766af7829e74025866ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fetching-data"></a>提取数据
打开数据源、 会话和行集对象后，你可以提取数据。 根据你使用的访问器的类型，你可能需要将列绑定。  
  
### <a name="to-fetch-data"></a>提取数据  
  
1.  打开使用相应的行集**打开**命令。  
  
2.  如果你使用`CManualAccessor`，绑定的输出列，如果尚未这样做。 若要将绑定列，请调用`GetColumnInfo`，然后创建使用绑定，访问器，如下面的示例中所示：  
  
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
  
3.  编写`while`循环来检索数据。 在循环中，调用`MoveNext`向前移动光标和测试，则为 S_OK，对返回的值，如下面的示例中所示：  
  
    ```  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
4.  在`while`循环中，你可以根据你的访问器类型提取数据。  
  
    -   如果你使用[CAccessor](../../data/oledb/caccessor-class.md)类，你应该具有包含数据成员的用户记录。 你可以访问使用这些数据成员，您的数据，如以下示例所示：  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   如果你使用`CDynamicAccessor`或`CDynamicParameterAccessor`类，你可以通过使用访问函数提取数据`GetValue`和`GetColumn`，下面的示例中所示。 如果你想要确定数据的类型使用，请使用`GetType`。  
  
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
  
    -   如果你使用`CManualAccessor`，你必须指定你自己的数据成员，将它们绑定你自己，并直接访问它们，如下面的示例中所示：  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## <a name="see-also"></a>请参阅  
 [使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)
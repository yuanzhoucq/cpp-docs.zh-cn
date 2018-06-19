---
title: 提供程序中设置属性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5d43e452d0fffcb4dc6eddcae722f8056dbd39dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109282"
---
# <a name="setting-properties-in-your-provider"></a>在提供程序中设置属性
查找所需的属性的属性组和属性 ID。 有关详细信息，请参阅[OLE DB 属性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)中*OLE DB 程序员参考*。  
  
 在由向导生成提供程序代码中，找到的属性组相对应的属性映射。 属性组的名称通常对应于对象的名称。 在命令或行集; 找不到命令和行集属性在数据源对象中找不到数据源和初始化属性。  
  
 在属性映射中，添加[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)宏。 PROPERTY_INFO_ENTRY_EX 采用四个参数：  
  
-   对您的属性相对应的属性 ID。 从属性名称开头，必须删除的前七个字符 ("DBPROP_")。 例如，如果你想要添加**DBPROP_MAXROWS**，传递`MAXROWS`为第一个元素。 如果这是自定义属性，传递的完整的 GUID 名称 (例如， `DBMYPROP_MYPROPERTY`)。  
  
-   变体类型的属性 (在[OLE DB 属性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)中*OLE DB 程序员参考*)。 输入**VT_** 类型 (如`VT_BOOL`或`VT_I2`) 与数据类型相对应。  
  
-   标志以指示属性是否读取和写入以及它所属的组。 例如，下面的代码指示属于行集组读/写属性：  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   属性的基值。 这可能是**VARIANT_FALSE**键入一个布尔值或零的整数类型，例如。 除非被更改，则该属性具有此值。  
  
    > [!NOTE]
    >  连接或链接到其他属性，如书签或更新某些属性。 当使用者将一个属性设置为 true 时，也可以设置另一个属性。 OLE DB 提供程序模板支持此方法通过[cutlprops:: Onpropertychanged](../../data/oledb/cutlprops-onpropertychanged.md)。  
  
## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>忽略的 Microsoft OLE DB 提供程序的属性  
 Microsoft OLE DB 提供程序忽略以下的 OLE DB 属性：  
  
-   **DBPROP_MAXROWS**仅适用于只读提供程序 （即，其中 DBPROP_IRowsetChange 和 DBPROP_IRowsetUpdate 均为 false）; 否则不支持此属性。  
  
-   **DBPROP_MAXPENDINGROWS**将被忽略; 提供程序指定其自己的限制。  
  
-   **DBPROP_MAXOPENROWS**将被忽略; 提供程序指定其自己的限制。  
  
-   **DBPROP_CANHOLDROWS**将被忽略; 提供程序指定其自己的限制。  
  
## <a name="see-also"></a>请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)
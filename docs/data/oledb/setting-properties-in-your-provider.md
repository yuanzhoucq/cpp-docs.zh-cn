---
title: "在提供程序中设置属性 | Microsoft Docs"
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
  - "OLE DB 提供程序, 属性"
  - "属性 [C++], OLE DB 提供程序"
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在提供程序中设置属性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

查找所需属性的属性组和属性 ID。  有关更多信息，请参见“OLE DB Programmer's Reference”（《OLE DB 程序员参考》）中的 [OLE DB 属性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)。  
  
 在由向导生成的提供程序代码中，查找与属性组相对应的属性映射。  属性组的名称通常与对象的名称相对应。  命令和行集合属性可在命令或行集合中找到；数据源和初始化属性可在数据源对象中找到。  
  
 在属性映射中，添加 [PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md) 宏。  PROPERTY\_INFO\_ENTRY\_EX 使用四个参数：  
  
-   与属性相对应的属性 ID。  必须将头七个字符 \("DBPROP\_"\) 从属性名的前面移除。  例如，如果要添加 **DBPROP\_MAXROWS**，将 `MAXROWS` 作为第一个元素传递。  如果这是自定义属性，传递完整的 GUID 名（例如，`DBMYPROP_MYPROPERTY`）。  
  
-   属性的 Variant 类型（在《OLE DB 程序员参考》中的 [OLE DB 属性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)中）。  输入与数据类型相对应的 **VT\_** 类型（如 `VT_BOOL` 或 `VT_I2`）。  
  
-   指示属性是否可读和可写及其所属的组的标志。  例如，以下代码指示属于行集合组的读\/写属性：  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   属性的基值。  例如，这对 Boolean 类型可能是 **VARIANT\_FALSE**，对 integer 类型可能是零。  除非被更改，属性将具有该值。  
  
    > [!NOTE]
    >  一些属性被连接或“链接”到其他属性，如书签或更新。  当使用者将一个属性设置为 true 时，另一个属性也可以设置。  OLE DB 提供程序模板通过 [CUtlProps::OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md) 方法支持此操作。  
  
## Microsoft OLE DB 提供程序忽略的属性  
 Microsoft OLE DB 提供程序忽略下面的 OLE DB 属性：  
  
-   **DBPROP\_MAXROWS** 仅适用于只读提供程序（即，DBPROP\_IRowsetChange 和 DBPROP\_IRowsetUpdate 为假的提供程序）；否则不支持此属性。  
  
-   忽略 **DBPROP\_MAXPENDINGROWS**；提供程序指定自己的限制。  
  
-   忽略 **DBPROP\_MAXOPENROWS**；提供程序指定自己的限制。  
  
-   忽略 **DBPROP\_CANHOLDROWS**；提供程序指定自己的限制。  
  
## 请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)
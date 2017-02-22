---
title: "将接口添加到提供程序 | Microsoft Docs"
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
  - "OLE DB 提供程序模板, 对象接口"
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 将接口添加到提供程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定要将接口添加到哪个对象（通常是“OLE DB 提供程序向导”创建的数据源、行集合、命令或会话对象）。  需要将接口添加到的对象可能是提供程序当前不支持的对象。  这种情况下，运行“ATL OLE DB 提供程序向导”创建对象。  右击“类视图”视图中的项目，从“添加”菜单中单击“添加类”，然后单击“ATL OLE DB 提供程序”。  可能需要将接口代码放在单独的目录中，然后将文件复制到提供程序项目。  
  
 如果创建了支持接口的新类，使对象从该类继承。  例如，可以将 **IRowsetIndexImpl** 类添加到行集合对象：  
  
```  
template <class Creator>  
class CAgentRowset :   
public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
   public IRowsetIndexImpl< ... >   
```  
  
 使用 COM\_INTERFACE\_ENTRY 宏将接口添加到对象中的 **COM\_MAP**。  如果没有映射，则创建一个。  例如：  
  
```  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
 对于行集合对象，链接其父对象的映射以便对象可以委托给父类。  在本例中，将 COM\_INTERFACE\_ENTRY\_CHAIN 宏添加到映射：  
  
```  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## 请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)
---
title: "CNoRowset 类 | Microsoft Docs"
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
  - "ATL.CNoRowset"
  - "ATL::CNoRowset<TAccessor>"
  - "CNoRowset"
  - "ATL.CNoRowset<TAccessor>"
  - "ATL::CNoRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoRowset 类"
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNoRowset 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对于[CCommand](../../data/oledb/ccommand-class.md) 或 [CTable](../../data/oledb/ctable-class.md) 可以用作模板参数 \(`TRowset`\) 。  
  
## 语法  
  
```  
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### 参数  
 `TAccessor`  
 一个访问器类  默认值为 `CAccessorBase`。  
  
## 备注  
 如果命令不返回行集合，请将 `CNoRowset` 用作模板参数。  
  
 `CNoRowset` 执行以下存根方法，每个对应于其他任何访问器类方法：  
  
-   **BindFinished** \- 指示绑定时完成的 \(返回 `S_OK`\)。  
  
-   **关闭** \- 释放列和当前 IRowset 接口。  
  
-   `GetIID` \- 检索的连接点接口 ID。  
  
-   **GetInterface** \- 检索接口。  
  
-   `GetInterfacePtr` \- 检索封装的接口指针。  
  
-   **SetAccessor** \- 设置为访问函数的指针。  
  
-   **SetupOptionalRowsetInterfaces** \- 将设置行集合的可选接口。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
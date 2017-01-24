---
title: "SET_PARAM_TYPE | Microsoft Docs"
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
  - "SET_PARAM_TYPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SET_PARAM_TYPE 宏"
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SET_PARAM_TYPE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定将遵循 `COLUMN_ENTRY` 宏输入、输出或输入\/输出的 `SET_PARAM_TYPE`。  
  
## 语法  
  
```  
  
SET_PARAM_TYPE(  
type  
 )  
  
```  
  
#### 参数  
 `type`  
 \[in\] 要为参数设置的类型。  
  
## 备注  
 提供程序仅支持基础数据源支持的参数输入\/输出类型。 类型是一个或多个 **DBPARAMIO** 值的组合（请参阅 *OLE DB 程序员参考* 中的 [DBBINDING 结构](https://msdn.microsoft.com/en-us/library/ms716845.aspx)）：  
  
-   **DBPARAMIO\_NOTPARAM** 访问器没有参数。 通常，将 **eParamIO** 设置为行访问器中的此值以提醒用户将忽略参数。  
  
-   **DBPARAMIO\_INPUT** 输入参数。  
  
-   **DBPARAMIO\_OUTPUT** 输出参数。  
  
-   **DBPARAMIO\_INPUT&#124;DBPARAMIO\_OUTPUT** 参数是输入和输出参数。  
  
## 示例  
 [!CODE [NVC_OLEDB_Consumer#18](../CodeSnippet/VS_Snippets_Cpp/NVC_OLEDB_Consumer#18)]  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)
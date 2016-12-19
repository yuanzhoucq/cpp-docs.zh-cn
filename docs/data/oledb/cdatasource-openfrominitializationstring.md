---
title: "CDataSource::OpenFromInitializationString | Microsoft Docs"
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
  - "CDataSource.OpenFromInitializationString"
  - "OpenFromInitializationString"
  - "CDataSource::OpenFromInitializationString"
  - "ATL::CDataSource::OpenFromInitializationString"
  - "ATL.CDataSource.OpenFromInitializationString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenFromInitializationString 方法"
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataSource::OpenFromInitializationString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

打开用户提供的初始化字符串指定的数据源。  
  
## 语法  
  
```  
  
      HRESULT OpenFromInitializationString(   
   LPCOLESTR szInitializationString,   
   bool fPromptForInfo = false    
) throw( );  
```  
  
#### 参数  
 *szInitializationString*  
 \[in\] 初始化字符串。  
  
 *fPromptForInfo*  
 \[in\] 如果此参数设置 **true**，则 `OpenFromInitializationString` 中将 **DBPROP\_INIT\_PROMPT** 属性设置为 **DBPROMPT\_COMPLETEREQUIRED**，指定想提示用户，只有当多为所需的信息。  这对于初始化字符串指定数据库需要密码的情况非常有用，但是，字符串不包含密码。  将提示用户输入密码 \(或其他\)，当缺少信息尝试连接到数据库时。  
  
 默认值为 **false**，指定从不提示用户 \(到 **DBPROMPT\_NOPROMPT**中设置 **DBPROP\_INIT\_PROMPT**。\)  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 使用在 oledb32.dll，的服务组件此方法以打开数据源对象；此 DLL 包含服务组件功能的实现 \(如合并资源，自动事务登记，依此类推。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)
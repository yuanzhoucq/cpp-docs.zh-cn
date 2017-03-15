---
title: "CDataSource::OpenWithPromptFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource.OpenWithPromptFileName"
  - "OpenWithPromptFileName"
  - "ATL::CDataSource::OpenWithPromptFileName"
  - "ATL.CDataSource.OpenWithPromptFileName"
  - "CDataSource::OpenWithPromptFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenWithPromptFileName 方法"
ms.assetid: 89460504-1aaf-4412-aa7b-fa5a4b39ada3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDataSource::OpenWithPromptFileName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此方法通过对话框提示用户，然后使用由用户指定的文件打开数据源。  
  
## 语法  
  
```  
  
        HRESULT OpenWithPromptFileName(   
   HWND hWnd = GetActiveWindow(   
   ),   
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,   
   LPCOLESTR szInitialDirectory = NULL    
) throw( );  
```  
  
#### 参数  
 `hWnd`  
 \[in\] 将成为对话框父级的窗口的句柄。  
  
 `dwPromptOptions`  
 \[in\] 确定要显示的定位器对话框的样式。  请参阅 Msdasc.h 了解可能的值。  
  
 *szInitialDirectory*  
 \[in\] 要在定位器对话框中显示的初始目录。  
  
## 返回值  
 一个标准 `HRESULT`。  
  
## 备注  
 此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。  有关详细信息，请访问 [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)，参阅“OLE DB 程序员参考”中的“OLE DB 服务”。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)
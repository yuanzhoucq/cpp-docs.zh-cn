---
title: "CDBErrorInfo::GetAllErrorInfo | Microsoft Docs"
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
  - "ATL.CDBErrorInfo.GetAllErrorInfo"
  - "CDBErrorInfo::GetAllErrorInfo"
  - "ATL::CDBErrorInfo::GetAllErrorInfo"
  - "GetAllErrorInfo"
  - "CDBErrorInfo.GetAllErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetAllErrorInfo 方法"
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDBErrorInfo::GetAllErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回在错误记录包含错误信息的所有类型。  
  
## 语法  
  
```  
  
      HRESULT GetAllErrorInfo(  
   ULONG ulRecordNum,  
   LCID lcid,  
   BSTR* pbstrDescription,  
   BSTR* pbstrSource = NULL,  
   GUID* pguid = NULL,  
   DWORD* pdwHelpContext = NULL,  
   BSTR* pbstrHelpFile = NULL  
) const throw( );  
```  
  
#### 参数  
 *ulRecordNum*  
 \[in\] 记录的从零开始的数字可以返回错误信息。  
  
 `lcid`  
 \[in\] 要返回错误信息的区域设置 ID。  
  
 `pbstrDescription`  
 \[out\] 为空或错误的文本说明的指针，如果不支持区域设置。  请参阅“备注”。  
  
 `pbstrSource`  
 \[out\] 到包含生成错误的组件名称的字符串的指针。  
  
 `pguid`  
 \[out\] 为定义错误的接口的 GUID 的指针。  
  
 *pdwHelpContext*  
 \[out\] 为帮助上下文 ID 的指针为 false。  
  
 *pbstrHelpFile*  
 \[out\] 到包含路径的字符串的指针到描述错误的帮助文件。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  为其他值返回查看 *OLE DB 程序员参考》\) 中的*[IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 备注  
 输出值 `pbstrDescription` 通过调用 IErrorInfo::GetDescription 内部可用，将值更改为 NULL，如果不支持区域设置，或者，如果以下两个条件皆为真时：  
  
1.  值 `lcid` 是非英语 \(美国和  
  
2.  `lcid` 的值不等于 GetUserDefaultLCID 返回的值。  
  
## 请参阅  
 [CDBErrorInfo 类](../../data/oledb/cdberrorinfo-class.md)
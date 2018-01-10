---
title: "Cdberrorinfo:: Getallerrorinfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
dev_langs: C++
helpviewer_keywords: GetAllErrorInfo method
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 46e233800f814b39e4e14f0b357c381a3e71311e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdberrorinfogetallerrorinfo"></a>CDBErrorInfo::GetAllErrorInfo
返回错误记录中包含的所有类型的错误信息。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 *ulRecordNum*  
 [in] 为其返回错误信息的记录的从零开始的数字。  
  
 `lcid`  
 [in] 要返回的错误信息的区域设置 ID。  
  
 `pbstrDescription`  
 [out] 当不支持区域设置时，指向错误或 NULL 的文本说明的指针。 请参阅“备注”。  
  
 `pbstrSource`  
 [out] 一个指针，该指针指向包含产生错误的组件的名称的字符串。  
  
 `pguid`  
 [out] 一个指针，该指针指向定义错误的接口的 GUID。  
  
 *pdwHelpContext*  
 [out] 指向错误的帮助上下文 ID 的指针。  
  
 *pbstrHelpFile*  
 [out] 一个指针，该指针指向包含描述错误的帮助文件的路径的字符串。  
  
## <a name="return-value"></a>返回值  
 `S_OK` 如果成功。 请参阅[ierrorrecords:: Geterrorinfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)中*OLE DB 程序员参考*有关其他返回值。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="remarks"></a>备注  
 `pbstrDescription` 的输出值通过调用 IErrorInfo::GetDescription 在内部获得，如果不支持区域设置或者同时满足以下两个条件，则此调用会将输出值设置为 NULL：  
  
1.  值`lcid`不是美国英语和  
  
2.  `lcid` 的值不等于 GetUserDefaultLCID 返回的值。  
  
## <a name="see-also"></a>请参阅  
 [CDBErrorInfo 类](../../data/oledb/cdberrorinfo-class.md)
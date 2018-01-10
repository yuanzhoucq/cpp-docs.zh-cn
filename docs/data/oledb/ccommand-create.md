---
title: "Ccommand:: Create |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.Create
- CCommand::Create
dev_langs: C++
helpviewer_keywords: Create method [C++]
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f4bbd236c2ec7ae6857ede1ac64f738ca8600774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccommandcreate"></a>CCommand::Create
调用[ccommand:: Createcommand](../../data/oledb/ccommand-createcommand.md)为指定的会话中，创建命令然后调用[ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)指定的命令文本。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
```  
  
#### <a name="parameters"></a>参数  
 `session`  
 [in]要在其中创建命令会话。  
  
 `wszCommand`  
 [in]指向命令字符串的 Unicode 文本的指针。  
  
 `szCommand`  
 [in]指向命令字符串的 ANSI 文本的指针。  
  
 `guidCommand`  
 [in]分析命令文本中指定的语法和一般规则要使用的提供程序的 GUID。 有关分支的说明，请参阅[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)中*OLE DB 程序员参考*。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 第一种形式的**创建**采用 Unicode 命令字符串。 第二种形式的**创建**采用 ANSI 命令字符串 （为了向后兼容现有的 ANSI 应用程序提供）。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)
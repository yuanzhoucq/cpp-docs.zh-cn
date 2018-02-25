---
title: "Ccommand:: Createcommand |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- CreateCommand method
ms.assetid: 3652a313-07a1-40ec-82d6-fc7182f2a6f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 60627b2e34798c5b1667c2f3bb7457c5a418a2dd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandcreatecommand"></a>CCommand::CreateCommand
创建新的命令。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 `session`  
 [in]A`CSession`要与新的命令相关联的对象。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法创建使用指定的会话对象的命令。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)
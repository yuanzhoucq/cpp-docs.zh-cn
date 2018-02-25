---
title: "Ccommand:: Releasecommand |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
dev_langs:
- C++
helpviewer_keywords:
- ReleaseCommand method
ms.assetid: 3b58230c-13d5-45c5-b43e-bb013ecc3019
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4fdfe9e901b81ee535522f42a54b91393df82af3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandreleasecommand"></a>CCommand::ReleaseCommand
释放参数访问器，然后释放命令本身。  
  
## <a name="syntax"></a>语法  
  
```cpp
void CCommandBase::ReleaseCommand() throw();  
  
```  
  
## <a name="remarks"></a>备注  
 `ReleaseCommand` 结合使用**关闭**。 请参阅[关闭](../../data/oledb/ccommand-close.md)有关用法的详细信息。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)   
 [CCommand::Close](../../data/oledb/ccommand-close.md)
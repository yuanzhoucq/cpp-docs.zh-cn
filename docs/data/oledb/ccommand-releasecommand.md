---
title: 'Ccommand:: Releasecommand |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a12b3fc3d12e79e93bd77bf02b6f7bfa87dc0052
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094873"
---
# <a name="ccommandreleasecommand"></a>CCommand::ReleaseCommand
释放参数访问器，然后释放命令本身。  
  
## <a name="syntax"></a>语法  
  
```cpp
void CCommandBase::ReleaseCommand() throw();  
  
```  
  
## <a name="remarks"></a>备注  
 `ReleaseCommand` 结合使用**关闭**。 请参阅[关闭](../../data/oledb/ccommand-close.md)有关用法的详细信息。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)   
 [CCommand::Close](../../data/oledb/ccommand-close.md)
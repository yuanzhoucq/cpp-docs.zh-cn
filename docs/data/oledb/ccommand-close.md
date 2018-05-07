---
title: 'Ccommand:: Close |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.Close
- CCommand::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5723c358e0af7cf9b92952bfd843ba90577333e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ccommandclose"></a>CCommand::Close
发布与命令关联的访问器行集。  
  
## <a name="syntax"></a>语法

```cpp
void Close();  
```  
  
## <a name="remarks"></a>备注  
 命令使用行集、结果集访问器和（可选的）参数访问器（与不支持参数并且不需要参数访问器的表不同）。  
  
 执行命令时，应请同时调用`Close`和[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)在命令后。  
  
 当您要重复执行同一命令时，您应通过在调用 `Close` 之前调用 `Execute` 来发布每个结果集访问器。 在序列末尾，应通过调用 `ReleaseCommand` 发布参数访问器。 另一种常见情形是调用具有输出参数的存储过程。 在很多提供程序（如 SQL Server 的 OLE DB 提供程序）上，输出参数值在你关闭结果集访问器前不可访问。 调用 `Close` 以关闭返回的行集和结果集访问器而不返回参数访问器，从而让您检索输出参数值。  
  
## <a name="example"></a>示例  
 以下示例演示在重复执行同一命令时如何调用 `Close` 和 `ReleaseCommand`。  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)
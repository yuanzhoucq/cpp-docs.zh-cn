---
title: DEFINE_COMMAND_EX |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND_EX
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2a77fa0d6655edeee88df3c7c45e1936a766b40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101037"
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 支持 Unicode 和 ANSI 应用程序。  
  
## <a name="syntax"></a>语法  
  
```cpp
DEFINE_COMMAND_EX(x, wszCommand)  
  
```  
  
#### <a name="parameters"></a>参数  
 *x*  
 [in]用户记录 （命令） 类的名称。  
  
 `wszCommand`  
 [in]将用于创建行集时使用的命令字符串[CCommand](../../data/oledb/ccommand-class.md)。  
  
## <a name="remarks"></a>备注  
 你指定的命令字符串将用作默认值，如果不指定中的命令文本[ccommand:: Open](../../data/oledb/ccommand-open.md)方法。  
  
 此宏接受 Unicode 字符串，而不考虑应用程序类型。 此宏是通过首选[DEFINE_COMMAND](../../data/oledb/define-command.md)因为它支持 Unicode 以及 ANSI 应用程序。  
  
## <a name="example"></a>示例  
 请参阅[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)
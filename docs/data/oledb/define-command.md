---
title: "DEFINE_COMMAND |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEFINE_COMMAND
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND macro
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f95fafbd9a63c5bf31add8bad1a8757bdcb60ae1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="definecommand"></a>DEFINE_COMMAND
指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 接受仅与指定的应用程序类型 （ANSI 或 Unicode） 匹配的字符串类型。  
  
> [!NOTE]
>  建议你使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是`DEFINE_COMMAND`。  
  
## <a name="syntax"></a>语法  
  
```cpp
DEFINE_COMMAND(x, szCommand)  
  
```  
  
#### <a name="parameters"></a>参数  
 *x*  
 [in]用户记录 （命令） 类的名称。  
  
 `szCommand`  
 [in]将用于创建行集时使用的命令字符串[CCommand](../../data/oledb/ccommand-class.md)。  
  
## <a name="remarks"></a>备注  
 你指定的命令字符串将用作默认值，如果不指定中的命令文本[ccommand:: Open](../../data/oledb/ccommand-open.md)方法。  
  
 如果生成为 Unicode 应用程序，此宏会接受 ANSI 字符串如果生成你的应用程序为 ANSI 或 Unicode 字符串。 建议你使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是`DEFINE_COMMAND`，因为前者接受 Unicode 字符串，而不考虑 ANSI 或 Unicode 应用程序类型。  
  
## <a name="example"></a>示例  
 请参阅[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)
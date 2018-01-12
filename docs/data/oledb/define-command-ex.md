---
title: "DEFINE_COMMAND_EX |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEFINE_COMMAND_EX
dev_langs: C++
helpviewer_keywords: DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 851b346c8fac955f1d82c0c43fdf75c4784ca04c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
指定将用于创建行集时使用的命令[CCommand](../../data/oledb/ccommand-class.md)类。 支持 Unicode 和 ANSI 应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
  
DEFINE_COMMAND_EX(  
x  
,   
wszCommand  
 )  
  
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
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)
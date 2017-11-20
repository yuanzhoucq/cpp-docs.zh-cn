---
title: "使用多个结果集从一个存储过程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 787c2123981f894eb4b6ba088cfcef774b6ed6f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>使用一个存储过程返回的多个结果集
大多数存储的过程返回多个结果集。 此类存储的过程通常包括一个或多个选择语句。 使用者需要考虑这一点以便处理所有结果集。  
  
### <a name="to-handle-multiple-result-sets"></a>若要处理多个结果集  
  
1.  创建`CCommand`类，该类具有`CMultipleResults`作为模板自变量和使用所选的访问器。 通常情况下，这是一个动态或手动访问器。 如果你使用另一种访问器，你可能不能以确定每个行集的输出列。  
  
2.  像往常一样执行存储的过程并将列绑定 (请参阅[How Do I 提取的数据？](../../data/oledb/fetching-data.md))。  
  
3.  使用的数据。  
  
4.  调用`GetNextResult`上`CCommand`类。 如果另一个结果行集不可用，`GetNextResult`返回，则为 S_OK，你应将列重新绑定，如果你使用手动访问器。 如果`GetNextResult`返回一个错误，没有任何进一步的结果设置可用。  
  
## <a name="see-also"></a>另请参阅  
 [使用存储过程](../../data/oledb/using-stored-procedures.md)
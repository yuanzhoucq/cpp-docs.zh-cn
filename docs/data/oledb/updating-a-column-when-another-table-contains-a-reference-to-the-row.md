---
title: "另一个表包含行引用时更新列 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cac57f2f4a1175fa1d9f4009e10fd3d0fae2a3b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>当另一个表包含行引用时更新列
某些提供程序可以检测哪些列入行更改时，但许多提供程序不能。 因此，更新的列可以导致错误时尝试更新行的引用。 若要解决此问题，请创建包含你想要更改的列单独的访问器。 应传递到该访问器数`SetData`。  
  
## <a name="see-also"></a>另请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)
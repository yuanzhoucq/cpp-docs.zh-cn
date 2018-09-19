---
title: 另一个表包含行引用时更新列 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6d2d3509b51d083290339514083a541ef9a86b64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030647"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>当另一个表包含行引用时更新列

某些提供程序可以检测哪些列的行更改，但很多提供程序不能。 结果是，更新列可能导致错误时尝试更新的行的引用。 若要解决此问题，请创建单独的访问器包含你想要更改的列。 传递到该访问器数`SetData`。  
  
## <a name="see-also"></a>请参阅  

[使用访问器](../../data/oledb/using-accessors.md)
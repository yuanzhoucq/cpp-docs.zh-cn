---
title: 另一个表包含行引用时更新列
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 46de5f54a3ec6525f779a6b55a700429a2a84fef
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039210"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>当另一个表包含行引用时更新列

某些提供程序可以检测哪些列的行更改，但很多提供程序不能。 结果是，更新列可能导致错误时对想要更新的行的引用。 若要解决此问题，请创建单独的访问器包含你想要更改的列。 传递到该访问器数`SetData`。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)
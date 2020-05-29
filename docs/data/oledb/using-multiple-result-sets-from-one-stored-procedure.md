---
title: 使用一个存储过程返回的多个结果集
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 6163eb8bf18edfc3d205f1d012de0c64c5570693
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209282"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>使用一个存储过程返回的多个结果集

大多数存储过程返回多个结果集。 此类存储过程通常包括一个或多个 select 语句。 使用者需要考虑这个包含来处理所有结果集。

## <a name="to-handle-multiple-result-sets"></a>处理多个结果集

1. 创建一个 `CCommand` 类，将其 `CMultipleResults` 为模板参数，并使用所选的访问器创建，通常为动态或手动访问器。 如果使用其他类型的访问器，则可能无法确定每个行集的输出列。

1. 照常执行存储过程并绑定列（请参阅[如何获取数据？](../../data/oledb/fetching-data.md)）。

1. 使用数据。

1. 对 `CCommand` 类调用 `GetNextResult`。 如果有另一个结果行集可用，`GetNextResult` 将返回 S_OK 并且如果使用手动访问器，则应重新绑定列。 如果 `GetNextResult` 返回错误，则没有其他结果集可用。

## <a name="see-also"></a>另请参阅

[使用存储过程](../../data/oledb/using-stored-procedures.md)

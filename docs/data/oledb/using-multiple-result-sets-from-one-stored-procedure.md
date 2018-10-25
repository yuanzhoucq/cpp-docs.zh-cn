---
title: 使用多个结果集从一个存储过程 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac30f74a593f79cea7f252c454f19b85260e27b8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078500"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>使用一个存储过程返回的多个结果集

大多数存储的过程返回多个结果集。 此类存储的过程通常包含一个或多个 select 语句。 使用者需要考虑此包含处理所有结果集。

## <a name="to-handle-multiple-result-sets"></a>若要处理多个结果集

1. 创建`CCommand`类的`CMultipleResults`作为模板参数和您的选择，通常一个动态或手动访问器的取值函数。 如果使用另一种类型的访问器，您可能不能以确定每个行集的输出列。

1. 像往常一样执行存储的过程并将列绑定 (请参阅[我如何提取的数据？](../../data/oledb/fetching-data.md))。

1. 使用的数据。

1. 调用`GetNextResult`上`CCommand`类。 如果另一个结果行集可用，`GetNextResult`返回 S_OK，并应重新绑定列，如果使用手动访问器。 如果`GetNextResult`返回一个错误，有没有更多结果集可用。

## <a name="see-also"></a>请参阅

[使用存储过程](../../data/oledb/using-stored-procedures.md)
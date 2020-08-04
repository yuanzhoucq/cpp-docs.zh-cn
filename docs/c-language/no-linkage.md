---
title: 无链接
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: a7c9a5b8f0ba92830500e55818093981a044d2df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218801"
---
# <a name="no-linkage"></a>无链接

如果块内某标识符的声明不包括 `extern` 存储类说明符，则此标识符没有链接，并且对函数是唯一的。

以下标识符没有链接：

- 声明为除对象或函数以外的任何项的标识符

- 声明为函数参数的标识符

- 声明不包含 `extern` 存储类说明符的对象的块范围标识符

如果标识符没有链接，那么在相同的范围级别内再次声明相同的名称（在声明符或类型说明符中）将产生符号重新定义错误。

## <a name="see-also"></a>请参阅

[使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)

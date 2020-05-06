---
title: 无链接
ms.date: 11/04/2016
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
ms.openlocfilehash: c80cb814145ac986864fe351e664d8472f3bf880
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232384"
---
# <a name="no-linkage"></a>无链接

如果块内的某个标识符的声明不包括 `extern` 存储类说明符，则该标识符没有链接并且对函数是唯一的。

以下标识符没有链接：

- 声明为除对象或函数以外的任何项的标识符

- 声明为函数参数的标识符

- 声明时未使用 `extern` 存储类说明符的对象的块范围标识符

如果标识符没有链接，那么在相同的范围级别内再次声明相同的名称（在声明符或类型说明符中）将产生符号重新定义错误。

## <a name="see-also"></a>请参阅

[使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)

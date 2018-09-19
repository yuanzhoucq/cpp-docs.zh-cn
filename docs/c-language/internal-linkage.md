---
title: 内部链接 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09b5a02b7892bff0233e37bbd63020a4d2904ec3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094203"
---
# <a name="internal-linkage"></a>内部链接

如果对象或函数的文件范围标识符声明包含 storage-class-specifier static，则该标识符具有内部链接。 否则，该标识符具有外部链接。 有关 storage-class-specifier 非终止符的讨论，请参阅[存储类](../c-language/c-storage-classes.md)。

在一个翻译单元内，带内部链接的标识符的每个实例均表示相同的标识符或函数。 内部链接的标识符对于翻译单元是唯一的。

## <a name="see-also"></a>请参阅

[使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)
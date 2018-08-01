---
title: abort 函数 |Microsoft Docs
ms.custom: ''
ms.date: 12/01/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5679ce718c564ee40fb07b676756ef79344a99
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403617"
---
# <a name="abort-function"></a>abort 函数

**中止**函数，同样在标准包含文件中声明\<stdlib.h >，将终止 C++ 程序。 之间的差异`exit`并**中止**在于`exit`可用于 c + + 运行时终止处理，才能开始 （全局对象将调用析构函数），而**中止**立即终止程序。 有关详细信息，请参阅[中止](../c-runtime-library/reference/abort.md)中*运行时库参考*。

## <a name="see-also"></a>请参阅
[程序终止](../cpp/program-termination.md)
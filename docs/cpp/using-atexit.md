---
title: 使用 atexit |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d5164394853d2ac4f18efc94863b8fc3fa5ba78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053123"
---
# <a name="using-atexit"></a>使用 atexit

与[atexit](../c-runtime-library/reference/atexit.md)函数，可以指定在程序终止之前执行 exit-processing 函数。 初始化之前调用了任何全局静态对象**atexit**在执行 exit-processing 函数之前销毁。

## <a name="see-also"></a>请参阅

[附加终止注意事项](../cpp/additional-termination-considerations.md)
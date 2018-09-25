---
title: 使用已存在的名称进行重命名 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: fc2a8f29-f757-4ce0-8d7f-7f8cff7f49ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10b9a9c4e42356a087c8cb6c10a470ba68acd4ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067749"
---
# <a name="renaming-with-a-name-that-exists"></a>使用已存在的名称进行重命名

**ANSI 4.9.4.2** 使用新名称的文件在调用 rename 函数之前存在的效果

如果尝试使用现有的名称重命名文件，则 rename 函数将失败并返回错误代码。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)
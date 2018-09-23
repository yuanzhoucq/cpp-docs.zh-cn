---
title: 寄存器：寄存器的可用性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- registers
ms.assetid: f6654e53-742c-4a30-8620-1a4d436a6ae4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9c7c09bccda07358384ca6b0be8d3ea824bc99e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055138"
---
# <a name="registers-availability-of-registers"></a>寄存器：寄存器的可用性

**ANSI 3.5.1** 通过使用寄存器存储类说明符可将对象实际放置在寄存器中的范围

编译器不接受对寄存器变量的用户请求。 相反，在进行优化时，它将自行做出选择。

## <a name="see-also"></a>请参阅

[实现定义的行为](../c-language/implementation-defined-behavior.md)
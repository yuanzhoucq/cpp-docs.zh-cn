---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 424ff295fe37e7c5ff02897a01b99a7c75876f85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397481"
---
# <a name="goto-masm"></a>GOTO (MASM)

将程序集传输**到标记为**"_macrolabel_" 的行。

## <a name="syntax"></a>语法

> **转**到*macrolabel*

## <a name="remarks"></a>备注

仅允许在[宏](macro.md)、[FOR](for-masm.md)、[强制](forc.md)、[重复](repeat.md)和[WHILE](while-masm.md)块中使用GOTO。 *Macrolabel*目标必须是行上唯一的指令，并且必须以前导冒号开头。

## <a name="see-also"></a>请参阅

[指令参考](directives-reference.md)

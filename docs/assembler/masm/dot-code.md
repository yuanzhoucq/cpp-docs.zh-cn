---
title: .CODE | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff2d66cfc79e84c8c4c7cf92e117c9ac8c84a555
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682482"
---
# <a name="code"></a>.CODE

与一起使用时[。模型](../../assembler/masm/dot-model.md)，指示在代码段的开始。

## <a name="syntax"></a>语法

> .代码 [[name]]

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`name`|可选参数，用于指定代码段的名称。 默认名称是小型、 小型、 简洁和平面 _TEXT[模型](../../assembler/masm/dot-model.md)。 默认名称是*modulename*_TEXT 对于其他模型。|

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>
[.DATA](../../assembler/masm/dot-data.md)<br/>
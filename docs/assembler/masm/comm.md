---
title: COMM |Microsoft 文档
ms.custom: ''
ms.date: 05/22/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1df6c729ab130a7ff38d7f7cf83224e7425e7dba
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2018
---
# <a name="comm"></a>COMM

与在指定的属性创建一个公用变量*定义*。

## <a name="syntax"></a>语法

> **COMM** *定义*[，*定义*]...

## <a name="remarks"></a>备注

公用变量由链接器，分配的并且无法初始化。 这意味着你不能依赖于位置或此类变量的序列。

每个*定义*具有以下形式：

[*langtype*] [**NEAR** &#124; **远处**]_标签_**:**_类型_[**:**_计数_]

可选*langtype*设置跟的名称的命名约定。 它将覆盖指定的任何语言 **。模型**指令。 可选**NEAR**或**远处**重写当前的内存模型。 *标签*是变量的名称。 *类型*可以是任何类型说明符 ([字节](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)，依次类推) 或一个整数，指定的字节数。 可选*计数*声明的数据对象中; 中指定的元素数的默认值为 1。

## <a name="example"></a>示例

该示例创建 512 字节元素的数组：

```masm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)

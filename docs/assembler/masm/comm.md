---
title: COMM |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 87bf6d91de052d7ecaf637100b455e66819c748b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690027"
---
# <a name="comm"></a>COMM

创建一个微乎其微的变量中指定的属性与*定义*。

## <a name="syntax"></a>语法

> **COMM** *定义*[，*定义*]...

## <a name="remarks"></a>备注

公用变量将分配由链接器，并且无法初始化。 这意味着您不能依赖于此类变量序列的位置。

每个*定义*具有以下形式：

[*langtype*] [**NEAR** &#124; **FAR**]_标签_**:**_类型_[**:**_计数_]

可选*langtype*设置跟的名称的命名约定。 它将替代指定的任何语言 **。模型**指令。 可选**NEAR**或**FAR**重写当前的内存模型。 *标签*是变量的名称。 *类型*可以是任何类型说明符 ([字节](../../assembler/masm/byte-masm.md)， [WORD](../../assembler/masm/word.md)，依次类推) 或一个整数，指定的字节数。 可选*计数*指定的元素数中声明的数据的对象; 默认值为 1。

## <a name="example"></a>示例

此示例创建一个 512 字节元素的数组：

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>

---
title: COMM
ms.date: 08/30/2018
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: d36161ba54ca80fc0f576c6f0a7c2a9410bf8075
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541037"
---
# <a name="comm"></a>COMM

使用在*定义*中指定的特性创建微乎其微变量。

## <a name="syntax"></a>语法

> **通信***定义*⟦ __，__ *定义*.。。⟧

## <a name="remarks"></a>备注

微乎其微变量由链接器分配，不能进行初始化。 这意味着不能依赖于此类变量的位置或序列。

每个*定义*都具有以下形式：

⟦*语言-类型*⟧⟦**NEAR** | **FAR**⟧ _label_ **：** _type_⟦ **：** _count_⟧

可选的*语言类型*为后面的名称设置命名约定。 它会重写由指定的任何语言 **。MODEL**指令。 可选的**NEAR**或**FAR**重写当前内存模型。 *标签*是变量的名称。 *类型*可以是任何类型说明符（[BYTE](../../assembler/masm/byte-masm.md)、 [WORD](../../assembler/masm/word.md)等），也可以是指定字节数的整数。 可选*计数*指定已声明的数据对象中的元素数。 默认*计数*为1。

## <a name="example"></a>示例

此示例将创建一个512字节元素数组：

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)

---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 0ea02806cae3295af0846baa6c4e9049d54c271b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75315168"
---
# <a name="comm"></a>COMM

使用在*定义*中指定的特性创建微乎其微变量。

## <a name="syntax"></a>语法

> **通信***定义*⟦ __，__ *定义*.。。⟧

## <a name="remarks"></a>备注

微乎其微变量由链接器分配，不能进行初始化。 这意味着不能依赖于此类变量的位置或序列。

每个*定义*都具有以下形式：

⟦*语言-类型*⟧⟦**NEAR** | **FAR**⟧ _label_ **：** _type_⟦ **：** _count_⟧

*Language 类型*、 **NEAR**和**FAR**参数仅在32位 MASM 中有效。

可选的*语言类型*为后面的名称设置命名约定。 它会重写由指定的任何语言 **。MODEL**指令。 可选的**NEAR**或**FAR**重写当前内存模型。 *标签*是变量的名称。 *类型*可以是任何类型说明符（[BYTE](byte-masm.md)、 [WORD](word.md)等），也可以是指定字节数的整数。 可选*计数*指定已声明的数据对象中的元素数。 默认*计数*为1。

## <a name="example"></a>示例

此示例将创建一个512字节元素数组：

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)

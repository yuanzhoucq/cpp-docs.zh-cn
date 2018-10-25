---
title: auto_inline |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs:
- C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc2fb4cb870ff1dca2f0b55e9aad20741ffb8220
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083173"
---
# <a name="autoinline"></a>auto_inline
排除范围内定义的所有函数其中**关闭**从正在被视为候选项为自动内联扩展中指定。

## <a name="syntax"></a>语法

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>备注

若要使用**auto_inline**杂注时，将其放置在之前和之后立即 （不在） 函数定义。 杂注在出现的位置后的第一个函数定义处生效。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
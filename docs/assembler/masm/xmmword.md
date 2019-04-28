---
title: XMMWORD
ms.date: 08/30/2018
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 59d1ba71260ed08b761c332e887cf27517762303
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210100"
---
# <a name="xmmword"></a>XMMWORD

使用 128 位多媒体操作数与 MMX 和 SSE (XMM) 说明。

## <a name="syntax"></a>语法

> XMMWORD

## <a name="remarks"></a>备注

`XMMWORD` 用于表示与相同的类型[__m128](../../cpp/m128.md)。

## <a name="example"></a>示例

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```
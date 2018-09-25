---
title: 位域的存储 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c39fa4455cfdc387ab5aa2068c80494a4a8810ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020077"
---
# <a name="storage-of-bit-fields"></a>位域的存储

**ANSI 3.5.2.1** int 内的位域的分配顺序

在整数中按照从最高有效位到最低有效位的顺序来分配位域。 在以下代码中

```
struct mybitfields
{
   unsigned a : 4;
   unsigned b : 5;
   unsigned c : 7;
} test;

int main( void )
{
   test.a = 2;
   test.b = 31;
   test.c = 0;
}
```

这些位将按如下所示排列：

```
00000001 11110010
cccccccb bbbbaaaa
```

由于 80x86 处理器将整数值的低字节存储在高字节之前，因此上面的整数 0x01F2 将按 0xF2 后跟 0x01 的形式存储在物理内存中。

## <a name="see-also"></a>请参阅

[结构、联合、枚举和位域](../c-language/structures-unions-enumerations-and-bit-fields.md)
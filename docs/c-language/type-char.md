---
title: char 类型 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b4db02292398da5c35f2894d4ce278cea88a584
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386824"
---
# <a name="type-char"></a>char 类型
`char` 类型用于存储可表示的字符集的成员的整数值。 该整数值是与指定字符对应的 ASCII 代码。  
  
 **Microsoft 专用**  
  
 类型 `unsigned char` 的字符值的范围介于 0 和 0xFF（十六进制）之间。 **signed char** 的范围介于 0x80 和 0x7F 之间。 这些范围分别转换为 0 到 255（十进制）以及 -128 到 +127（十进制）。 /J 编译器选项将默认值从 **signed** 更改为 `unsigned`。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [基本类型的存储](../c-language/storage-of-basic-types.md)
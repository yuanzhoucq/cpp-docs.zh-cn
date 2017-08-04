---
title: "C 调整了大小的整数类型 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: db04c6862be26d5641a485c47ac7fd71b43d16fe
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="c-sized-integer-types"></a>C 调整了大小的整型
**Microsoft 专用**  
  
 Microsoft C 支持固定大小整数类型。 可以使用 __intn 类型说明符声明 8 位、16 位、32 位或 64 位整数变量，其中 n 是整数变量的大小（以位为单位）。 n 的值可以是 8、16、32 或 64。 以下示例为四种类型的固定大小整数各声明了一个变量：  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 固定大小整数的前三种类型是大小相同的 ANSI 类型的同义词，用于编写在多个平台中具有相同的行为的可移植代码。 请注意，__int8 数据类型与 char 类型是同义词，\__int16 与 short 类型是同义词，\__int32 与 int 类型是同义词。 \__int64 类型没有等效的 ANSI 匹配项。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [基本类型的存储](../c-language/storage-of-basic-types.md)

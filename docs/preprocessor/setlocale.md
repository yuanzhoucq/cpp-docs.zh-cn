---
title: setlocale | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
dev_langs:
- C++
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c52697fffb27e6fd25936f3c6566f027cc265c18
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="setlocale"></a>setlocale
定义要在转换宽字符常量和字符串时使用的区域设置（国家/地区和语言）。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma setlocale( "[locale-string]" )  
```  
  
## <a name="remarks"></a>备注  
 由于将多字节字符转换为宽字符的算法可能因区域设置而异，并且编译可能在不同于运行可执行文件的区域设置中进行，因此此杂注提供了在编译时指定目标区域设置的方法。 这将确保宽字符字符串以正确的格式存储。  
  
 默认值*区域设置字符串*是""。  
  
 “C”区域设置会将字符串中的每个字符作为 `wchar_t` (unsigned short) 映射到“C”区域设置的值。 可用于其他值`setlocale`中找到的项[语言字符串](../c-runtime-library/language-strings.md)列表。 例如，您可以发出：  
  
```  
#pragma setlocale("dutch")  
```  
  
 能否发出语言字符串取决于计算机上是否支持相应的代码页和语言 ID。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
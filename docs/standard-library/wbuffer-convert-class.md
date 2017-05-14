---
title: "wbuffer_convert 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::cvt::wbuffer_convert
- wbuffer_convert
- cvt::wbuffer_convert
- wbuffer/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 20
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 8efbf80606e1196b7376a264e63b87e89e07b53d
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="wbufferconvert-class"></a>wbuffer_convert 类
描述用于控制元素与字节流缓冲区之间的来回传输的流缓冲区。  
  
## <a name="syntax"></a>语法  
  
```
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Codecvt`|表示转换对象的[区域设置](../standard-library/locale-class.md)方面。|  
|`Elem`|宽字符元素类型。|  
|`Traits`|与 Elem 关联的特征。|  
  
## <a name="remarks"></a>备注  
 此模板类描述对 `_Elem` 类型的元素（其字符特征由类 `Traits` 描述）与 `std::streambuf` 类型的字节流缓冲区之间的来回传输进行控制的流缓冲区。  
  
 一系列 `Elem` 值与多字节序列之间的转换由类 `Codecvt<Elem, char, std::mbstate_t>` 的对象执行，这符合标准代码转换方面 `std::codecvt<Elem, char, std::mbstate_t>` 的要求。  
  
 此模板类的对象存储：  
  
-   指向其基础字节流缓冲区的指针  
  
-   指向分配的转换对象（在销毁 [wbuffer_convert](../standard-library/wbuffer-convert-class.md) 对象时释放）的指针


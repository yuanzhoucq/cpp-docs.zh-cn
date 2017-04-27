---
title: __crtLCMapStringW | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __crtLCMapStringW
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __crtLCMapStringW
dev_langs:
- C++
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 115e77a6451bc29eaaa7bed45105825b990d68cf
ms.lasthandoff: 04/01/2017

---
# <a name="crtlcmapstringw"></a>__crtLCMapStringW
将一个字符串映射到另一个字符串，以执行指定的与区域设置相关的转换。 此函数还可用于生成输入字符串的排序键。  
  
## <a name="syntax"></a>语法  
  
```cpp  
int __crtLCMapStringW(  
   LCID    Locale,  
   DWORD   dwMapFlags,  
   LPCWSTR lpSrcStr,  
   int     cchSrc,  
   LPWSTR  lpDestStr,  
   int     cchDest)  
```  
  
#### <a name="parameters"></a>参数  
 `Locale`  
 区域设置标识符。 区域设置为字符串映射或排序键生成提供上下文。 应用程序可使用 `MAKELCID` 宏创建区域设置标识符。  
  
 `dwMapFlags`  
 在字符串或排序键生成期间要使用的转换的类型。  
  
 `lpSrcStr`  
 指向函数映射或用于排序键生成的源字符串的指针。 假定此参数为 Unicode 字符串。  
  
 `cchSrc`  
 由 `lpSrcStr` 参数指向的字符串的大小（以字符为单位）。 此计数可包含 NULL 终止符，也可不包含它。  
  
 `cchSrc` 值 -1 指定由 `lpSrcStr` 指向的字符串是以 null 结尾的。 如果是这种情况而且此函数在使用时采用了字符串映射模式，则此函数会自己计算字符串的长度，并以 null 终止存储在 `*lpDestStr`中的映射字符串。  
  
 `lpDestStr`  
 指向函数将映射字符串或排序键存储到其中的缓冲区的长指针。  
  
 `cchDest`  
 由 `lpDestStr`指向的缓冲区的大小（以字符为单位）。  
  
## <a name="return-value"></a>返回值  
 如果 `cchDest` 的值不为零，则写入到缓冲区的字符数（如果指定了 `LCMAP_SORTKEY` ，则为字节数）表示成功。 此计数包括 NULL 终止符的空间。  
  
 如果 `cchDest` 值为零，则接收转换的字符串或排序键所需的缓冲区大小（以字符为单位，如果指定了 `LCMAP_SORTKEY` ，则以字节为单位）表示成功。 此大小包括 NULL 终止符的空间。  
  
 零表示失败。 若要获得扩展的错误信息，请调用 `GetLastError` 函数。  
  
## <a name="remarks"></a>备注  
 如果 `cchSrc` 大于零且 `lpSrcStr` 是一个以 null 结尾的字符串，则 `__crtLCMapStringW` 将 `cchSrc` 设置为字符串的长度。 然后， `__crtLCMapStringW` 使用指定的参数调用 `LCMapString` 函数的宽字符串 (Unicode) 版本。 有关此函数的参数和返回值的详细信息，请参阅 `LCMapString` MSDN 库 [中的](http://go.microsoft.com/fwlink/?linkID=150542)函数。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|__crtLCMapStringW|awint.h|

---
title: "&lt; &gt; codecvt | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "codecvt"
  - "std::<codecvt>"
  - "std.<codecvt>"
  - "<codecvt>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt 标头"
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; &gt; codecvt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义描述基于模板类对象的多个模板类 [codecvt](../standard-library/codecvt-class.md)。 这些对象可以用作 [区域设置 facet](../standard-library/locale-class.md#facet_class) 控制的类型的值序列之间的转换 `Elem` 和类型的值序列 `char`。  
  
## <a name="syntax"></a>语法  
  
```  
#include <codecvt>  
  
```  
  
## <a name="remarks"></a>备注  
 在此标头中声明的区域设置 facet 几个字符编码之间进行转换。 对宽字符 （存储在固定大小的整数中的程序）︰  
  
-   Ucs-4 是在程序内部编码的 unicode 编码 (ISO 10646)  
  
-   UCS 4 是 Unicode (ISO 10646) 编码为一个 32 位整数程序内。  
  
-   Ucs-2 是 Unicode 编码在程序中  
  
-   UCS 2 是 Unicode 编码为 16 位整数程序内。  
  
-   UTF 16 是 Unicode 编码在其中一种方法的程序  
  
-   UTF 16 是 Unicode 编码在程序中，为一个或两个 16 位整数。 （请注意这不符合有效范围内的字符编码标准的 C 或标准 c + + 的所有要求。 不过它广泛使用，因此。）  
  
 字节流 (存储在文件中、 作为字节序列，传输或存储在数组中的程序中的 `char`):  
  
-   Utf-8 是 Unicode 编码  
  
-   Utf-8 是 Unicode 编码字节流中，为具有确定性的字节顺序的一个或多个八位字节。  
  
-   UTF 16LE 是 Unicode 编码  
  
-   UTF 16LE 是 Unicode 编码为 utf-16 字节流中与第一次显示为两个八位字节，减少不重要的字节的每个 16 位整数。  
  
-   UTF 16BE 是 Unicode 编码  
  
-   UTF 16BE 是 Unicode 编码为 utf-16 字节流中与第一次显示为两个八位字节，更重要的字节的每个 16 位整数。  
  
### <a name="enumerations"></a>枚举  
  
|||  
|-|-|  
|[codecvt_mode](../Topic/%3Ccodecvt%3E%20enums.md#codecvt_mode_enumeration)|指定的区域设置 facet 的配置信息。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[codecvt_utf8](../Topic/%3Ccodecvt%3E%20functions.md#codecvt_utf8)|表示一个区域设置 facet，编码为 ucs-2 或 ucs-4，宽字符和字节流为 utf-8 编码之间进行转换。|  
|[codecvt_utf8_utf16](%3Ccodecvt%3E%20functions.md#codecvt_utf8_utf16)|表示一个区域设置 facet，编码为 utf-16 的宽字符和字节流为 utf-8 编码之间进行转换。|  
|[codecvt_utf16](../Topic/%3Ccodecvt%3E%20functions.md#codecvt_utf16)|表示一个区域设置 facet，宽字符为 ucs-2 或 ucs-4 编码和字节流编码为 UTF 16LE 或 UTF 16BE 之间进行转换。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< codecvt>  
  
 **Namespace:** stdt  
  
## <a name="see-also"></a>请参阅  
 [标头文件引用](../standard-library/cpp-standard-library-header-files.md)





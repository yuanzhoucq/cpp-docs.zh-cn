---
title: 数据类型范围 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d55a2102299957a40cd9f742f91868ee2b5b849b
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407671"
---
# <a name="data-type-ranges"></a>数据类型范围
Visual C++ 32 位和 64 位编译器可识别本文后面的表中的类型。  
  
-   `int` (`unsigned int`)  
  
-   `__int8` (`unsigned __int8`)  
  
-   `__int16` (`unsigned __int16`)  
  
-   `__int32` (`unsigned __int32`)  
  
-   `__int64` (`unsigned __int64`)  
  
-   `short` (`unsigned short`)  
  
-   `long` (`unsigned long`)  
  
-   `long` `long` (`unsigned long long`)  
  
 如果其名称以两个下划线 (`__`) 开始，则数据类型是非标准的。  
  
 下表中指定的范围均包含起始值和结束值。  
  
|类型名称|字节|其他名称|值的范围|  
|---------------|-----------|-----------------|---------------------|  
|**int**|4|**signed**|-2,147,483,648 到 2,147,483,647|  
|**unsigned int**|4|**unsigned**|0 到 4,294,967,295|  
|**__int8**|1|**char**|-128 到 127|  
|**无符号的 __int8**|1|**unsigned char**|0 到 255|  
|**__int16**|2|**短**，**短 int**，**签名 short int**|-32,768 到 32,767|  
|**无符号的 __int16**|2|**无符号 short**，**无符号短整数**|0 到 65,535|  
|**__int32**|4|**签名**，**带符号整型**， **int**|-2,147,483,648 到 2,147,483,647|  
|**无符号的 __int32**|4|**无符号**，**无符号的整数**|0 到 4,294,967,295|  
|**__int64**|8|**超长**，**长长签名**|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|  
|unsigned __int64|8|**无符号 long long**|0 到 18,446,744,073,709,551,615|  
|**bool**|1|无|**false**或 **，则返回 true**|  
|**char**|1|无|-默认情况下 128 到 127<br /><br /> 0 到 255（当使用 [/J](../build/reference/j-default-char-type-is-unsigned.md)编译时）|  
|**有符号的字符**|1|无|-128 到 127|  
|**unsigned char**|1|无|0 到 255|  
|**short**|2|**短整型**，**签名 short int**|-32,768 到 32,767|  
|**unsigned short**|2|**unsigned short int**|0 到 65,535|  
|**long**|4|**long int**，**带符号长整型**|-2,147,483,648 到 2,147,483,647|  
|**unsigned long**|4|**unsigned long int**|0 到 4,294,967,295|  
|**long long**|8|无 (但等效于 **__int64**)|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|  
|**无符号 long long**|8|无 (但等效于**unsigned 的 __int64**)|0 到 18,446,744,073,709,551,615|  
|**enum**|varies|无| |  
|**float**|4|无|3.4E +/- 38（7 位数）|  
|**double**|8|无|1.7E +/- 308（15 位数）|  
|**long double**|与相同**双精度**|无|与相同**双精度**|  
|**wchar_t**|2|**__wchar_t**|0 到 65,535|  
  
 根据使用方式、 的变量 **__wchar_t**指定宽字符类型或多字节字符类型。 在字符或字符串常量前使用 `L` 前缀以指定宽字符类型常量。  
  
 **签名**并**无符号**是可用于除任何整型类型的修饰符**bool**。 请注意， **char**，**签名 char**，并**unsigned char**的重载和模板等机制而言是三个不同的类型。  
  
 **Int**并**无符号的 int**类型具有四个字节的大小。 但是，可移植代码不应依赖于的大小**int**由于语言标准允许可特定于实现的。  
  
 Visual Studio 中的 C/C++ 还支持按大小分类的整型。 有关详细信息，请参阅 [__int8、\__int16、 \__int32、 \__int64](../cpp/int8-int16-int32-int64.md) 和 [整数限制](../cpp/integer-limits.md)。  
  
 有关每个类型的大小限制的详细信息，请参阅[基本类型](../cpp/fundamental-types-cpp.md)。  
  
 枚举类型的范围因语言上下文和指定的编译器标志而异。 有关详细信息，请参阅 [C 枚举声明](../c-language/c-enumeration-declarations.md) 和 [枚举](../cpp/enumerations-cpp.md)。  
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)
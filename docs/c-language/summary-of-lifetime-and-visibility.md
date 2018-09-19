---
title: 生存期和可见性摘要 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcda68906e281bdf33ebe95a8019851bcb3cdb11
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752295"
---
# <a name="summary-of-lifetime-and-visibility"></a>生存期和可见性的摘要
下表是大多数标识符的生存期和可见性特征的摘要。 前三列提供了定义生存期和可见性的特性。 具有前三列提供的特性的标识符具有在第四和第五列中显示的生存期和可见性。 但是，该表未涵盖所有可能的情况。 有关详细信息，请参考[存储类](../c-language/c-storage-classes.md)。  
  
### <a name="summary-of-lifetime-and-visibility"></a>生存期和可见性的摘要  
  
|特性：<br /><br /> 级别|项|存储类<br /><br /> 说明符|结果:<br /><br /> 生存期|可见性|  
|---------------------------|----------|----------------------------------|--------------------------|----------------|  
|文件范围|变量定义|**static**|Global|此项所在的源文件的剩余部分|  
||变量声明|**extern**|Global|此项所在的源文件的剩余部分|  
||函数原型或定义|**static**|Global|单个源文件|  
||函数原型|**extern**|Global|源文件的剩余部分|  
|块范围|变量声明|**extern**|Global|块|  
||变量定义|**static**|Global|块|  
||变量定义|auto 或 register|本地|块|  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
以下示例演示了变量的块、嵌套和可见性：  
  
### <a name="code"></a>代码  
  
```  
// Lifetime_and_Visibility.c  
  
#include <stdio.h>  
  
int i = 1;  // i defined at external level  
  
int main()  // main function defined at external level  
{  
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)  
    {                                 // Begin first nested block  
        int i = 2, j = 3;          // i and j defined at internal level  
        printf_s( "%d %d\n", i, j );  // Prints 2, 3  
        {                             // Begin second nested block  
            int i = 0;                // i is redefined  
            printf_s( "%d %d\n", i, j ); // Prints 0, 3  
        }                             // End of second nested block  
        printf_s( "%d\n", i );        // Prints 2 (outer definition  
                                      //  restored)  
    }                                 // End of first nested block  
    printf_s( "%d\n", i );            // Prints 1 (external level  
                                      // definition restored)  
    return 0;  
}   
```  
  
### <a name="comments"></a>注释  
在此示例中，有四个级别的可见性：外部级别和三个块级别。 值将输出到屏幕中，如每个语句后面的注释中所述。  
  
## <a name="see-also"></a>请参阅  
[生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)
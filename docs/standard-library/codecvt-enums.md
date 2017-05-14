---
title: "&lt;codecvt&gt; enums | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
caps.latest.revision: 10
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 268723c43d61761e2b0a01d337adecc3336e01f3
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; 枚举
  
##  <a name="codecvt_mode"></a>  codecvt_mode 枚举  
 指定 [locale](../standard-library/locale-class.md) facet 的配置信息。  
  
```  
enum codecvt_mode {  
    consume_header = 4,  
    generate_header = 2,  
    little_endian = 1  
 };  
```  
  
### <a name="remarks"></a>备注  
 枚举定义为 [\<codecvt>](../standard-library/codecvt.md) 中声明的区域设置 facet 提供配置信息的三个常量。 非重复值为：  
  
- `consume_header`，在读取多字节序列时使用初始标头序列，并确定要读取的后续多字节序列的字节顺序  
  
- `generate_header`，在写入多字节序列时生成初始标头序列，以播发要编写的后续多字节序列的字节顺序  
  
- `little_endian`，在 little-endian 顺序中，而不是在默认 big endian 顺序中生成多字节序列  
  
 这些常量可以任意组合并用“OR”连在一起。  
  
## <a name="see-also"></a>另请参阅  
 [\<codecvt>](../standard-library/codecvt.md)



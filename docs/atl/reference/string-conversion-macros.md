---
title: "字符串转换宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
caps.latest.revision: 16
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
translationtype: Machine Translation
ms.sourcegitcommit: 89790d1a56f64e6479ae32d72c529142ba8df1de
ms.openlocfilehash: 0dce243b0f7db087db908d603e6cd1cfc4b02db8
ms.lasthandoff: 02/24/2017

---
# <a name="string-conversion-macros"></a>字符串转换宏
这些宏提供字符串转换功能。  
  
|||  
|-|-|  
|[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)|组的宏的字符串类型之间转换。|  
|[DEVMODE 和 TEXTMETRIC 字符串转换宏](http://msdn.microsoft.com/library/85cebec0-2a18-48e5-9c1c-99d5b7f15425)|组将在此字符串转换宏`DEVMODE`和`TEXTMETRIC`结构。|  
  
##  <a name="a-nameatlandmfcstringconversionmacrosa--atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a>ATL 和 MFC 字符串转换宏  
 此处讨论的字符串转换宏对 ATL 和 MFC 都有效。 有关 MFC 字符串转换的详细信息，请参阅[TN059︰ 使用 MFC MBCS/Unicode 转换宏](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)和[MFC 宏和全局](../../mfc/reference/mfc-macros-and-globals.md)。  
  
##  <a name="a-namedevmodeandtextmetricstringconversionmacrosa--devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE 和 TEXTMETRIC 字符串转换宏  
 这些宏创建一份[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)或[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)结构，并将新的结构中的字符串转换为新的字符串类型。 宏为新结构分配到堆栈上的内存，并返回指向新结构的指针。  
  
```
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>备注  
 例如:   
  
 [!code-cpp[NVC_ATL_Utilities #&128;](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
 and：  
  
 [!code-cpp[NVC_ATL_Utilities #&129;](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
 在宏名称中，源结构中的字符串类型是在左边 (例如， **A**) 和目标结构中的字符串类型是在右边 (例如， **W**)。 **A** stands for **LPSTR**, **OLE** stands for `LPOLESTR`, **T** stands for `LPTSTR`, and **W** stands for `LPWSTR`.  
  
 因此，`DEVMODEA2W`副本`DEVMODE`结构与**LPSTR**字符串到`DEVMODE`结构与`LPWSTR`字符串`TEXTMETRICOLE2T`副本`TEXTMETRIC`结构与`LPOLESTR`字符串到`TEXTMETRIC`结构与`LPTSTR`字符串，依次类推。  
  
 转换中的两个字符串`DEVMODE`结构不是设备名称 ( **dmDeviceName**) 和窗体名称 ( **dmFormName**)。 `DEVMODE`字符串转换宏还更新结构大小 ( **dmSize**)。  
  
 转换中的四个字符串`TEXTMETRIC`结构不是第一个字符 ( **tmFirstChar**)，最后一个字符 ( **tmLastChar**)，默认的字符 ( **tmDefaultChar**)，和换行符字符 ( **tmBreakChar**)。  
  
 行为`DEVMODE`和`TEXTMETRIC`字符串转换宏取决于编译器指令起作用，如果有的话。 如果源和目标类型相同，则不发生转换。 编译器指令更改**T**和**OLE** ，如下所示︰  
  
|有效的编译器指令|T 变为|OLE 变为|  
|----------------------------------|---------------|-----------------|  
|无|**A**|**W**|  
|**_UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**_UNICODE**和**OLE2ANSI**|**W**|**A**|  
  
 下表列出`DEVMODE`和`TEXTMETRIC`字符串转换宏。  
  
### <a name="devmode-and-textmetric-string-conversion-macros"></a>DEVMODE 和 TEXTMETRIC 字符串转换宏  
  
|||  
|-|-|  
|`DEVMODEA2W`|`TEXTMETRICA2W`|  
|`DEVMODEOLE2T`|`TEXTMETRICOLE2T`|  
|`DEVMODET2OLE`|`TEXTMETRICT2OLE`|  
|`DEVMODEW2A`|`TEXTMETRICW2A`|  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)



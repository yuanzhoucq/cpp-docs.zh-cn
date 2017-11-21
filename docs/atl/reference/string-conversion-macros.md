---
title: "字符串转换宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
dev_langs: C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ee1abce5c319d3efdc8154304c4d5ec853e0e517
ms.sourcegitcommit: ce115fcfb20b4fbc198f0f7b6d0ca3e94d7ce947
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="string-conversion-macros"></a>字符串转换宏

这些宏提供字符串转换功能。  
 
##  <a name="atl_and_mfc_string_conversion_macros"></a>ATL 和 MFC 字符串转换宏

此处讨论的字符串转换宏对 ATL 和 MFC 都有效。 有关 MFC 字符串转换的详细信息，请参阅[TN059： 使用 MFC MBCS/Unicode 转换宏](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)和[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)。

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE 和 TEXTMETRIC 字符串转换宏

这些宏创建一份[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)或[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)结构并将新的结构中的字符串转换为新的字符串类型。 宏为新的结构分配堆栈上的内存，并返回指向新的结构的指针。  
  
```cpp
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>备注

例如:   
  
[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
and：  
  
[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
在宏名称中，源结构中的字符串类型位于左侧 (例如， **A**) 和目标结构中的字符串类型位于右侧 (例如， **W**)。 **A**代表`LPSTR`， **OLE**代表`LPOLESTR`， **T**代表`LPTSTR`，和**W**代表`LPWSTR`。  
  
因此， **DEVMODEA2W**副本`DEVMODE`结构`LPSTR`字符串到`DEVMODE`结构`LPWSTR`字符串， **TEXTMETRICOLE2T**复制`TEXTMETRIC`结构`LPOLESTR`字符串到`TEXTMETRIC`结构`LPTSTR`字符串，依次类推。  
  
转换中的两个字符串`DEVMODE`结构不是设备名称 (`dmDeviceName`) 和窗体名称 (`dmFormName`)。 `DEVMODE`字符串转换宏还更新结构大小 (`dmSize`)。  
  
转换中的四个字符串`TEXTMETRIC`结构不是第一个字符 (`tmFirstChar`)，最后一个字符 (`tmLastChar`)，默认字符 (`tmDefaultChar`)，和中断字符 (`tmBreakChar`)。
  
行为`DEVMODE`和`TEXTMETRIC`字符串转换宏取决于编译器指令起作用，如果有。 如果源和目标类型相同，则不发生转换。 编译器指令更改**T**和**OLE** ，如下所示：  
  
|有效的编译器指令|T 变为|OLE 变为|  
|----------------------------------|---------------|-----------------|  
|无|**A**|**W**|  
|**\_UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**\_UNICODE**和**OLE2ANSI**|**W**|**A**|  
  
 下表列出`DEVMODE`和`TEXTMETRIC`字符串转换宏。  
  
|||  
|-|-|  
|`DEVMODEA2W`|`TEXTMETRICA2W`|  
|`DEVMODEOLE2T`|`TEXTMETRICOLE2T`|  
|`DEVMODET2OLE`|`TEXTMETRICT2OLE`|  
|`DEVMODEW2A`|`TEXTMETRICW2A`|  

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)

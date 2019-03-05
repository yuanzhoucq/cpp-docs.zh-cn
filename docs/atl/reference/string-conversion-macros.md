---
title: 字符串转换宏
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: 889f8459e81418197420bc2efd410225d4f220bc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271757"
---
# <a name="string-conversion-macros"></a>字符串转换宏

这些宏提供字符串转换功能。

##  <a name="atl_and_mfc_string_conversion_macros"></a>  ATL 和 MFC 字符串转换宏

此处讨论的字符串转换宏对 ATL 和 MFC 都有效。 有关 MFC 字符串转换的详细信息，请参阅[TN059:使用 MFC MBCS/Unicode 转换宏](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)并[MFC 宏和全局](../../mfc/reference/mfc-macros-and-globals.md)。

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  DEVMODE 和 TEXTMETRIC 字符串转换宏

这些宏创建一份[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)或[TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica)结构，并将新的结构中的字符串转换为新的字符串类型。 宏为新的结构分配在堆栈上的内存，并返回指向新结构的指针。

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>备注

例如：

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

and：

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

在宏名称中的源结构的字符串类型位于左侧 (例如， **A**) 和目标结构中的字符串类型是在右侧 (例如， **W**)。 **一个**LPSTR，代表**OLE** LPOLESTR，代表**T**代表 LPTSTR，和**W**代表 LPWSTR。

DEVMODEA2W 将因此，复制`DEVMODE`LPSTR 结构字符串到`DEVMODE`LPWSTR 字符串，TEXTMETRICOLE2T 副本具有结构`TEXTMETRIC`LPOLESTR 结构字符串到`TEXTMETRIC`结构与 LPTSTR 字符串和其他操作。

两个字符串中转换`DEVMODE`结构是设备名称 (`dmDeviceName`) 和窗体名称 (`dmFormName`)。 `DEVMODE`字符串转换宏还更新结构大小 (`dmSize`)。

转换中的四个字符串`TEXTMETRIC`结构是第一个字符 (`tmFirstChar`)，最后一个字符 (`tmLastChar`)，默认的字符 (`tmDefaultChar`)，和换行符字符 (`tmBreakChar`)。

行为`DEVMODE`和`TEXTMETRIC`字符串转换宏取决于编译器指令中的效果，如果有。 如果源和目标类型相同，则不发生转换。 编译器指令更改**T**并**OLE** ，如下所示：

|有效的编译器指令|T 变为|OLE 变为|
|----------------------------------|---------------|-----------------|
|无|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|**\_UNICODE**和**OLE2ANSI**|**W**|**A**|

下表列出`DEVMODE`和`TEXTMETRIC`字符串转换宏。

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)

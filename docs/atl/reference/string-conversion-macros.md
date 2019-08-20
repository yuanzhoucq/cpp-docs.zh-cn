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
ms.openlocfilehash: 6a84424de81eba2e6ab1e1baf60f567ebf2739ee
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915506"
---
# <a name="string-conversion-macros"></a>字符串转换宏

这些宏提供字符串转换功能。

##  <a name="atl_and_mfc_string_conversion_macros"></a>ATL 和 MFC 字符串转换宏

此处讨论的字符串转换宏对 ATL 和 MFC 都有效。 有关 MFC 字符串转换的详细信息, 请[参阅 TN059:使用 mfc MBCS/Unicode 转换宏](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)和[mfc 宏和全局](../../mfc/reference/mfc-macros-and-globals.md)。

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE 和 TEXTMETRIC 字符串转换宏

这些宏创建[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)或[TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica)结构的副本, 并将新结构中的字符串转换为新的字符串类型。 宏为新结构在堆栈上分配内存, 并返回指向新结构的指针。

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>备注

例如:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

and：

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

在宏名称中, 源结构中的字符串类型位于左侧 (例如, **A**), 目标结构中的字符串类型位于右侧 (例如**W**)。 代表 LPSTR, **OLE**代表 LPOLESTR, **T**代表 LPTSTR, **W**代表 LPWSTR。

因此, DEVMODEA2W 将包含`DEVMODE` LPSTR 字符串的结构复制到`DEVMODE`包含 LPWSTR `TEXTMETRIC`字符串的结构中, TEXTMETRICOLE2T 将包含 LPOLESTR 字符串的结构`TEXTMETRIC`复制到包含 LPTSTR 字符串的结构中, 等等。

在`DEVMODE`结构中转换的两个字符串是设备名称 (`dmDeviceName`) 和窗体名称 (`dmFormName`)。 字符串转换宏还会更新结构大小 (`dmSize`)。 `DEVMODE`

在`TEXTMETRIC`结构中转换的四个字符串分别为第一个`tmFirstChar`字符 ()、最后一个`tmLastChar`字符 ()、默认字符`tmDefaultChar`() 和分隔字符 (`tmBreakChar`)。

`DEVMODE` 和`TEXTMETRIC`字符串转换宏的行为取决于有效的编译器指令 (如果有)。 如果源和目标类型相同，则不发生转换。 编译器指令更改**T**和**OLE** , 如下所示:

|有效的编译器指令|T 变为|OLE 变为|
|----------------------------------|---------------|-----------------|
|无|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|UNICODE 和**OLE2ANSI**  **\_**|**W**|**A**|

下表列出了`DEVMODE`和`TEXTMETRIC`字符串转换宏。

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)

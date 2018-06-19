---
title: DEVNAMES 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3234df2f0430ea75399791f4fd88a636a63b67e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371473"
---
# <a name="devnames-structure"></a>DEVNAMES 结构
`DEVNAMES` 结构包含标识打印机的驱动程序、设备和输出端口名称的字符串。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagDEVNAMES { /* dvnm */  
    WORD wDriverOffset;  
    WORD wDeviceOffset;  
    WORD wOutputOffset;  
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */  
} DEVNAMES;  
```  
  
#### <a name="parameters"></a>参数  
 *wDriverOffset*  
 （输入/输出）指定字符相对于包含设备驱动程序文件名（无扩展名）的不以 null 结尾的字符串的偏移量。 对于输入，此字符串用于确定打印机最初显示在对话框中。  
  
 *wDeviceOffset*  
 （输入/输出）指定字符相对于包含设备名称的以 null 结尾的字符串（最大值为包含 null 的 32 个字节）的偏移量。 此字符串必须与相同**dmDeviceName**的成员[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)结构。  
  
 *wOutputOffset*  
 （输入/输出）指定字符相对于包含物理输出媒体（输出端口）的 DOS 设备名称的以 null 结尾的字符串的偏移量。  
  
 *wDefault*  
 指定 `DEVNAMES` 结构中包含的字符串是否标识默认打印机。 此字符串用于验证默认打印机自上次打印操作以来是否更改。 对于输入，如果**DN_DEFAULTPRN**中设置标志，其他值`DEVNAMES`针对当前默认打印机检查结构。 如果任意字符串不匹配，则将显示警告消息，通知用户文档可能需要重新设置格式。 在输出时， **wDefault**成员发生变化时，仅当显示打印设置对话框中，且用户选择确定按钮。 **DN_DEFAULTPRN**如果选择默认打印机设置标志。 如果选择特定打印机，则将不会设置此标志。 此成员的所有其他位将保留供“打印对话框”过程内部使用。  
  
## <a name="remarks"></a>备注  
 **PrintDlg**函数使用这些字符串初始化系统定义打印对话框中的成员。 当用户关闭对话框后，此结构中将返回有关选定打印机的信息。  
  
## <a name="requirements"></a>要求  
 **标头：** commdlg.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)



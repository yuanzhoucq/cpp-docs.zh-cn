---
title: "CIPAddressCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
dev_langs:
- C++
helpviewer_keywords:
- IP address control
- Internet address edit box
- CIPAddressCtrl class
- Internet protocol address box
- common controls, Internet Explorer 4.0
- Internet Explorer 4.0 common controls
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b3849580c7bfd07f241e55cc48144959566d7d09
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl 类
提供 Windows 公共 IP 地址控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|构造 `CIPAddressCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CIPAddressCtrl::ClearAddress](#clearaddress)|清除 IP 地址控件的内容。|  
|[CIPAddressCtrl::Create](#create)|创建 IP 地址控件，并将其附加到`CIPAddressCtrl`对象。|  
|[CIPAddressCtrl::CreateEx](#createex)|创建具有指定的 Windows 扩展样式的 IP 地址控件并将其附加到`CIPAddressCtrl`对象。|  
|[CIPAddressCtrl::GetAddress](#getaddress)|检索 IP 地址控件中的所有四个字段的地址值。|  
|[CIPAddressCtrl::IsBlank](#isblank)|确定 IP 地址控件中的所有字段都为空。|  
|[CIPAddressCtrl::SetAddress](#setaddress)|设置 IP 地址控件中的所有四个字段的地址值。|  
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|将键盘焦点设置为 IP 地址控件中指定的字段。|  
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|设置 IP 地址控件中指定的字段的范围。|  
  
## <a name="remarks"></a>备注  
 IP 地址控件的控件类似于一个编辑控件，也允许您输入和操作中 Internet 协议 (IP) 格式的数字地址。  
  
 此控件 (并因此`CIPAddressCtrl`类) 仅适用于运行在 Microsoft Internet Explorer 4.0 及更高版本的程序。 它们还将在未来版本的 Windows 和 Windows NT 下可用。  
  
 有关 IP 地址控件的详细信息，请参阅[IP 地址控件](http://msdn.microsoft.com/library/windows/desktop/bb761372)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl  
 创建一个 `CIPAddressCtrl` 对象。  
  
```  
CIPAddressCtrl();
```  
  
##  <a name="clearaddress"></a>CIPAddressCtrl::ClearAddress  
 清除 IP 地址控件的内容。  
  
```  
void ClearAddress();
```  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[IPM_CLEARADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761377)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="create"></a>CIPAddressCtrl::Create  
 创建 IP 地址控件，并将其附加到`CIPAddressCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 IP 地址控件的样式。 适用窗口样式的组合。 必须包括**WS_CHILD**因为该控件必须是子窗口的样式。 请参阅[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关 windows 样式的列表。  
  
 `rect`  
 对 IP 地址控件的大小和位置的引用。 它可为[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 指向 IP 地址控件的父窗口的指针。 它不能**NULL。**  
  
 `nID`  
 IP 地址控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CIPAddressCtrl`两个步骤中的对象。  
  
1.  调用构造函数，创建`CIPAddressCtrl`对象。  
  
2.  调用**创建**，后者可创建 IP 地址控件。  
  
 如果您想要扩展的窗口样式用于您的控件，调用[CreateEx](#createex)而不是**创建**。  
  
##  <a name="createex"></a>CIPAddressCtrl::CreateEx  
 调用此函数可创建的控件 （子窗口），并将其与关联`CIPAddressCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 IP 地址控件的样式。 适用窗口样式的组合。 必须包括**WS_CHILD**因为该控件必须是子窗口的样式。 请参阅[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关 windows 样式的列表。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
##  <a name="getaddress"></a>CIPAddressCtrl::GetAddress  
 检索 IP 地址控件中的所有四个字段的地址值。  
  
```  
int GetAddress(
    BYTE& nField0,  
    BYTE& nField1,  
    BYTE& nField2,  
    BYTE& nField3);  
  
int GetAddress(DWORD& dwAddress);
```  
  
### <a name="parameters"></a>参数  
 `nField0`  
 字段 0 值对发件人已打包的 IP 地址的引用。  
  
 `nField1`  
 对字段 1 值来自已打包的 IP 地址的引用。  
  
 `nField2`  
 为字段 2 值来自已打包的 IP 地址的引用。  
  
 `nField3`  
 对字段 3 值来自已打包的 IP 地址的引用。  
  
 `dwAddress`  
 为地址的引用`DWORD`接收的 IP 地址的值。 请参阅**备注**的表，其中显示如何`dwAddress`进行填充。  
  
### <a name="return-value"></a>返回值  
 在 IP 地址控件中的非空字段数。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在第一个原型更高版本中，域 0 到 3 之间的控件中读取的数字左到右分别，填充的四个参数。 在上面的第二个原型`dwAddress`，如下所示填充。  
  
|字段|包含的字段值的位|  
|-----------|-------------------------------------|  
|0|24 到 31 之间|  
|1|16 到 23|  
|2|8 到 15|  
|3|0 到 7|  
  
##  <a name="isblank"></a>CIPAddressCtrl::IsBlank  
 确定 IP 地址控件中的所有字段都为空。  
  
```  
BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果所有的 IP 地址控件字段都是空，则为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[IPM_ISBLANK](http://msdn.microsoft.com/library/windows/desktop/bb761379)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setaddress"></a>CIPAddressCtrl::SetAddress  
 设置 IP 地址控件中的所有四个字段的地址值。  
  
```  
void SetAddress(
    BYTE nField0,  
    BYTE nField1,  
    BYTE nField2,  
    BYTE nField3);  
  
void SetAddress(DWORD dwAddress);
```  
  
### <a name="parameters"></a>参数  
 `nField0`  
 从已打包的 IP 地址的字段 0 值。  
  
 `nField1`  
 从已打包的 IP 地址的字段 1 值。  
  
 `nField2`  
 从已打包的 IP 地址的字段 2 值。  
  
 `nField3`  
 从已打包的 IP 地址的字段 3 值。  
  
 `dwAddress`  
 一个`DWORD`值，该值包含新的 IP 地址。 请参阅**备注**的表，其中显示了`DWORD`填充值。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在第一个原型更高版本中，域 0 到 3 之间的控件中读取的数字左到右分别，填充的四个参数。 在上面的第二个原型`dwAddress`，如下所示填充。  
  
|字段|包含的字段值的位|  
|-----------|-------------------------------------|  
|0|24 到 31 之间|  
|1|16 到 23|  
|2|8 到 15|  
|3|0 到 7|  
  
##  <a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus  
 将键盘焦点设置为 IP 地址控件中指定的字段。  
  
```  
void SetFieldFocus(WORD nField);
```  
  
### <a name="parameters"></a>参数  
 `nField`  
 从零开始的字段焦点应设置为的索引。 如果此值大于字段数，则会将焦点设置到第一个空白字段。 如果所有字段都均非空，则会将焦点设置到第一个字段。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[IPM_SETFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb761381)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange  
 设置 IP 地址控件中指定的字段的范围。  
  
```  
void SetFieldRange(
    int nField,  
    BYTE nLower,  
    BYTE nUpper);
```  
  
### <a name="parameters"></a>参数  
 `nField`  
 将应用范围的从零开始的字段索引。  
  
 `nLower`  
 对接收此 IP 地址控件中的指定字段的下限的整数的引用。  
  
 `nUpper`  
 对接收此 IP 地址控件中的指定字段的上限的整数的引用。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[IPM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761382)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 使用两个参数，`nLower`和`nUpper`，以指示该字段的下限和上限限制而不是*wRange* Win32 消息所使用的参数。  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)





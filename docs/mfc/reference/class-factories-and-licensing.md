---
title: 类工厂和许可
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: e3fed6520cdbe0fd964e4e80e7c9ed9b78296d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372300"
---
# <a name="class-factories-and-licensing"></a>类工厂和许可

为了创建 OLE 控件的实例，容器应用程序调用了控件的类工厂的成员函数。 由于控件是实际 OLE 对象，类工厂将负责创建控件的实例。 每个 OLE 控件类必须有一个类工厂。

OLE 控件的另一个重要功能是强制使用许可证。 ControlWizard 可让您在控件项目的创建过程中包含授权。 有关控件许可的详细信息，请参阅[ActiveX 控件：许可 ActiveX 控件](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)。

下表列出了用于声明和实现控件的类工厂以及为控件授权的几个宏和函数。

### <a name="class-factories-and-licensing"></a>类工厂和许可

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|声明 OLE 控件或属性页的类工厂。|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|实现控件的 `GetClassID` 函数并声明类工厂的实例。|
|[BEGIN_OLEFACTORY](#begin_olefactory)|开始任何授权函数的声明。|
|[END_OLEFACTORY](#end_olefactory)|结束任何授权函数的声明。|
|[AfxVerifyLicFile](#afxverifylicfile)|确认控件是否已获得在特定计算机上使用的授权。|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

声明类工厂和控制类`GetClassID`的成员函数。

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
控件类的名称。

### <a name="remarks"></a>备注

对于不支持许可的控件，在控件类标头文件中使用此宏。

请注意，此宏的作用与以下代码示例相同：

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

实现控件的类工厂和控制类的[GetClassID](../../mfc/reference/colecontrol-class.md#getclassid)成员函数。

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>参数

*class_name*<br/>
控件属性页类的名称。

*external_name*<br/>
公开给应用程序的对象名称。

*l， w1， w2， b1， b2， b3， b4， b5， b6， b7， b8*<br/>
类 CLSID 的组件。 有关这些参数的详细信息，请参阅[IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)的备注。

### <a name="remarks"></a>备注

对于使用DECLARE_OLECREATE_EX宏或BEGIN_OLEFACTORY和END_OLEFACTORY宏的任何控件类，此宏必须出现在实现文件中。 外部名称是受其他应用程序公开的 OLE 控件的标识符。 容器使用此名称请求此控件类的对象。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a>BEGIN_OLEFACTORY

在控件类的标头文件中开始类工厂的声明。

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
指定类出厂的控件类的名称。

### <a name="remarks"></a>备注

类工厂许可功能的声明应在BEGIN_OLEFACTORY后立即开始。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="end_olefactory"></a><a name="end_olefactory"></a>END_OLEFACTORY

结束控件的类工厂的声明。

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>参数

*class_name*<br/>
类工厂是控件类的名称。

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a>Afx验证文件

调用此函数以验证所`pszLicFileName`命名的许可证文件是否对 OLE 控件有效。

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>参数

*hInstance*<br/>
与许可控件关联的 DLL 的实例句柄。

*psslic文件名称*<br/>
指向包含许可证文件名的 null 终止字符串。

*psslic文件内容*<br/>
指向必须匹配许可证文件开头找到的序列的字节序列。

*cch*<br/>
*pszlicFile内容中的*字符数。

### <a name="return-value"></a>返回值

如果许可证文件存在，并且以*pszLicFile内容*中的字符序列开头，则非零;否则 0。

### <a name="remarks"></a>备注

如果*cch*为 -1，则此功能使用：

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>要求

  **头**afxctl.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

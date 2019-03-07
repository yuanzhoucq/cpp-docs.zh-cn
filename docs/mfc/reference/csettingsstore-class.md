---
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: 1de26ceedfd29f276693be512bd41f169fb44b94
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274539"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

包装 Windows API 函数，提供用于访问注册表的面向对象的接口。

## <a name="syntax"></a>语法

```
class CSettingsStore : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|构造 `CSettingsStore` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSettingsStore::Close](#close)|关闭打开注册表项。|
|[CSettingsStore::CreateKey](#createkey)|打开指定的密钥或创建它，如果不存在。|
|[CSettingsStore::DeleteKey](#deletekey)|删除指定的密钥及其所有子级。|
|[CSettingsStore::DeleteValue](#deletevalue)|删除打开密钥的指定的值。|
|[CSettingsStore::Open](#open)|打开指定的密钥。|
|[CSettingsStore::Read](#read)|检索指定的密钥值的数据。|
|[CSettingsStore::Write](#write)|向下打开的注册表的注册表中写入值。|

## <a name="remarks"></a>备注

成员函数`CreateKey`和`Open`非常相似。 如果已存在的注册表项，`CreateKey`和`Open`函数相同的方式。 但是，如果注册表项不存在，则`CreateKey`将创建它，而`Open`将返回错误值。

## <a name="example"></a>示例

下面的示例演示如何使用的打开和读取方法`CSettingsStore`类。 此代码片段属于[工具提示演示示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>要求

**标头：** afxsettingsstore.h

##  <a name="close"></a>  CSettingsStore::Close

关闭打开注册表项。

```
virtual void Close();
```

### <a name="remarks"></a>备注

默认情况下，此方法调用的析构函数从[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)。

##  <a name="createkey"></a>  CSettingsStore::CreateKey

打开注册表项或不存在时创建该队列。

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
[in]指定创建或打开密钥的名称。

### <a name="return-value"></a>返回值

如果成功，则为 0否则为一个非零值。

### <a name="remarks"></a>备注

`CreateKey` 使用`m_hKey`作为根的注册表的查询。 它会搜索*pszPath*作为子项的`m_hKey`。 如果不存在该键，`CreateKey`创建它。 否则，它打开的密钥。 `CreateKey` 然后设置`m_hKey`到创建或打开密钥。

##  <a name="csettingsstore"></a>  CSettingsStore::CSettingsStore

创建一个 `CSettngsStore` 对象。

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>参数

*bAdmin*<br/>
[in]布尔参数，用于指定是否`CSettingsStore`对象在管理员模式下起作用。

*bReadOnly*<br/>
[in]布尔参数，用于指定是否`CSettingsStore`在只读模式下创建对象。

### <a name="remarks"></a>备注

如果*bAdmin*设置为 TRUE，`m_hKey`成员变量设置为**HKEY_LOCAL_MACHINE**。 如果您设置*bAdmin*为 FALSE，`m_hKey`设置为**HKEY_CURRENT_USER**。

安全访问权限取决于*bReadOnly*参数。 如果*bReadonly*为 FALSE 时，安全访问权限将设置为**KEY_ALL_ACCESS**。 如果*bReadyOnly*为 TRUE 时，安全访问权限将设置为的组合**KEY_QUERY_VALUE、 KEY_NOTIFY**并**KEY_ENUMERATE_SUB_KEYS**。 有关安全访问以及注册表的详细信息，请参阅[注册表项安全和访问权限](/windows/desktop/SysInfo/registry-key-security-and-access-rights)。

析构函数`CSettingsStore`释放`m_hKey`自动。

##  <a name="deletekey"></a>  CSettingsStore::DeleteKey

从注册表中删除密钥及其所有子级。

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
[in]若要删除的密钥的名称。

*bAdmin*<br/>
[in]指定要删除的密钥的位置的开关。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果此方法将失败`CSettingsStore`对象处于只读模式。

如果将参数*bAdmin*为零，`DeleteKey`搜索要删除下的键**HKEY_CURRENT_USER**。 如果*bAdmin*为非零值，`DeleteKey`搜索要删除下的键**HKEY_LOCAL_MACHINE**。

##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue

删除从值`m_hKey`。

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>参数

*pszValue*<br/>
[in]指定要移除的值字段。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="open"></a>  CSettingsStore::Open

打开注册表项。

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>参数

*pszPath*<br/>
[in]注册表项的名称。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此方法成功打开指定的密钥后，它会设置`m_hKey`到此密钥的句柄。

##  <a name="read"></a>  CSettingsStore::Read

从注册表中读取的值。

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>参数

*pszKey*<br/>
[in]包含要从注册表中读取的值的名称的以 null 结尾的字符串指针。

*iVal*<br/>
[out]对接收从注册表项中读取的值的整数变量的引用。

*dwVal*<br/>
[out]一个 32 位双字变量来接收从注册表项中读取的值对的引用。

*sVal*<br/>
[out]一个字符串变量来接收从注册表项中读取的值对的引用。

*scStringList*<br/>
[out]一个字符串列表变量来接收从注册表项中读取的值对的引用。

*scArray*<br/>
[out]一个字符串数组变量来接收从注册表项中读取的值对的引用。

*dwcArray*<br/>
[out]一个 32 位双字数组变量来接收从注册表项中读取的值对的引用。

*wcArray*<br/>
[out]对一个 16 位字数组变量来接收从注册表项中读取的值的引用。

*bcArray*<br/>
[out]对一个字节数组变量来接收从注册表项中读取的值的引用。

*lpPoint*<br/>
[out]引用指向`POINT`从注册表项读取收到的值的结构。

*rect*<br/>
[out]引用[CRect](../../atl-mfc-shared/reference/crect-class.md)从注册表项读取收到的值的变量。

*ppData*<br/>
[out]从注册表项读取指针到指向接收的值的数据。

*pBytes*<br/>
[out]指向无符号的整数变量的指针。 此变量接收缓冲区的大小， *ppData*指向。

*list*<br/>
[out]引用[CObList](../../mfc/reference/coblist-class.md)从注册表项读取收到的值的变量。

*obj*<br/>
[out]引用[CObject](../../mfc/reference/cobject-class.md)从注册表项读取收到的值的变量。

*pObj*<br/>
[out]引用指向`CObject`从注册表项读取收到的值的变量。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`Read` 检查*pszKey*作为子项的`m_hKey`。

##  <a name="write"></a>  CSettingsStore::Write

向下打开的注册表的注册表中写入值。

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>参数

*pszKey*<br/>
[in]包含要设置的值的名称的字符串指针。

*iVal*<br/>
[in]对包含要存储的数据的整数变量的引用。

*dwVal*<br/>
[in]对包含要存储的数据的 32 位双字变量引用。

*pszVal*<br/>
[in]指向包含要存储的数据的以 null 结尾的字符串变量的指针。

*scStringList*<br/>
[in]引用[CStringList](../../mfc/reference/cstringlist-class.md)变量包含要存储的数据。

*bcArray*<br/>
[in]对包含要存储的数据的字节数组变量的引用。

*scArray*<br/>
[in]对包含要存储的数据的字符串数组变量的引用。

*dwcArray*<br/>
[in]对包含要存储的数据的 32 位双字数组变量的引用。

*wcArray*<br/>
[in]对包含要存储的数据的 16 位字数组变量的引用。

*rect*<br/>
[in]引用[CRect](../../atl-mfc-shared/reference/crect-class.md)变量包含要存储的数据。

*lpPoint*<br/>
[in]引用指向`POINT`变量包含要存储的数据。

*pData*<br/>
[in]指向包含要存储的数据的缓冲区的指针。

*nBytes*<br/>
[in]指定的大小，以字节为单位的数据*pData*参数所指向。

*list*<br/>
[in]引用[CObList](../../mfc/reference/coblist-class.md)变量包含要存储的数据。

*obj*<br/>
[in]引用[CObject](../../mfc/reference/cobject-class.md)变量包含要存储的数据。

*pObj*<br/>
[in]指针到指向`CObject`变量包含要存储的数据。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

若要写入到注册表，必须设置*bReadOnly*为非零值在创建时[CSettingsStore](../../mfc/reference/csettingsstore-class.md)对象。 有关详细信息，请参阅[CSettingsStore::CSettingsStore](#csettingsstore)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)

[TOC]

## 目的

> 仿照GoLink实现一个UI页面

## 实现流程

### 1. 实现自定义组件

> 自定义框架
> 属性和事件处理(键盘识别)

#### 1.1 自定义框架

```c++
class SMyWindow :
	public SWindow
{
	SOUI_CLASS_NAME(SMyWindow, L"mywindow");
public:
	SMyWindow();
	~SMyWindow();
};
```

#### 1.2 响应键盘消息

```c++
MSG_WM_KEYDOWN(OnKeyDown)
```

#### 1.3 响应鼠标消息

```c++
MSG_WM_LBUTTONDOWN(OnLButtonDown)
```

#### 1.4 添加自定义属性

```c++
BOOL m_bHandleEnter;

SOUI_ATTRS_BEGIN()
    ATTR_BOOL(L"handleEnter", m_bHandleEnter, FALSE)
    SOUI_ATTRS_END()
```

#### 1.5 添加自定义事件

```c++
// 类定义
class EventKeyEnter : public TplEventArgs<EventKeyEnter>
{
    SOUI_CLASS_NAME(EventKeyEnter, L"on_key_enter")
        public:
    enum {EventID = EVT_EXTERNAL_BEGIN+500};
    EventKeyEnter(SObject* pSender) :TplEventArgs<EventKeyEnter>(pSender) {
        data = 0;
    }

    int data;
};

// 触发
EventKeyEnter evt(this);
SStringW strEvtName1 = evt.GetName();
STRACEA("EvtName: %s", S_CW2A(strEvtName1));
evt.data = 100;
FireEvent(evt);

// 注册
EVENT_NAME_HANDLER(L"edit_test", EventKeyEnter::EventID, OnEditEnter)
```

### 2. 布局

> SOUI 布局全部采用相对坐标，由 pos,offset(pos2type), size, width,height 这几个个窗 口属性配合指定。 size, width, height 属性 size, width, height 比较简单，是用来指定窗口的大小的，只有在 pos 属性指定的值个数 不为 4 时生效。 size 是 2014 年底增加的布局属性，size="width,height"。

#### 2.1 pos 属性

> 目前支持 7 种标志：|,%,[,],{,},@

| 标志 |                             解释                             |
| :--: | :----------------------------------------------------------: |
|  \|  |                   代表参考父窗口的中心；如                   |
|  %   | 代表在父窗口的百分比，可以是小数，负数。如：%40 代表在父窗口的 40%位 置，%-40 则等价于(1-40%) |
|  [   | 相对于前一兄弟窗口。用于 X 时，参考前一兄弟窗口的 right，用于 Y 时参考前一兄 弟窗口的 bottom |
|  ]   | 相对于后一兄弟窗口。用于 X 时，参考后一兄弟的 left,用于 Y 时参考后一兄弟的 top |
|  {   | 相对于前一兄弟窗口。用于 X 时，参考前一兄弟窗口的 left，用于 Y 时参考前一兄弟 窗口的 top |
|  }   | 相对于后一兄弟窗口。用于 X 时，参考后一兄弟的 right,用于 Y 时参考后一兄弟的 bottom |
|  @   | 标志用来指定窗口的大小，只能出现在 pos 属性的第 3，4 个值中，用来标识窗口 的宽度。当后面的值为负时，代表自动计算窗口的宽度或者高度（2015.3.3 新增加解 释） |

#### 2.2 offset 属性

> offset 属性包含两个值，用来代表窗口在通过其它布局属性完成后的偏移量：如 offset="-1,-1"，该 offset 表明窗口向左方及上方各平衡一个窗口大小的单位。

### 3. 基本控件使用

#### 3.1 静态文本控件

```shell

```

### 3. 实现多语言切换

### 4. 实现主题切换

### 4. RTSP视频播放
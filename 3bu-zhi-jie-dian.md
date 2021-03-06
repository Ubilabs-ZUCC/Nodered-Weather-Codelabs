# 三、布置节点

OK！完成了最基本的 Hello World！那就让我们开始布置我们的节点吧！如果你足够幸运，那么你将走到这个 codelab 的最后，并且制作出一个简单气象站显示界面！

首先，我会告诉你，我给你的物联网数据结构是这样的：

```
"{"tmp": "15", "loc": "16", "wind_spd": "0", "hum": "84", "pcpn": "0", "fl": "16", "pres": "1022"}"
```

这些数据是哪里来的？当然是我们的物联网底层数据，作为一个简易气象站，我们已经能够利用这些数据建立我们的气象信息显示界面了！

我们把这个“Debug”节点从左侧拖出来

![](/assets/snipaste_20171026_015845.png)

我不会告诉你，这个模块是非常重要又毫无用处的。因为他在我们建立逻辑的时候可以帮助我们调试，在我们建立好逻辑后他就是个废物。现在我们这个 codelab 是带着大家建立一个逻辑结构，所以我还是放上了这个节点，这个节点可以与任意一个节点相连接，然后点击“部署”，就像我上一回合“Hello World”的中那样将时间戳输出到“Debug”界面一样，你开始观测刚刚连接的这个节点会输出什么。如果你有兴趣，可以跟着我进行这个 codelab 的时候，是不是利用这个节点去看看某个节点输出什么，哈哈！

和第二回合一样，将 mqtt out 节点从拖出来并选择刚刚配置好的Server，并填好你的Topic

![](/assets/snipaste_20171026_020616.png)

拖出“json”节点，并将 mqtt out 节点和“json”节点连接。

![](/assets/snipaste_20171026_020940.png)

从“Function”类中拖出“Function”节点，并双击，在“Name”一栏中填写`tmp`，这个“Name”是我们自己给取的，这里写“tmp”是为了方便辨识，因为我们有如此多的数据。之后，在“Function”中编辑我们的 JavaScript 代码。不要怕，我给你写好了，况且也就两行，你就复制粘贴就好！

```
msg.payload = msg.payload.tmp;
return msg;
```

然后点击右上角的“完成”

![](/assets/snipaste_20171026_021314.png)

将“json”节点和名为“tmp”的“Function”节点连接，后从“Dashboard”类中将“Gauge”拖出来，双击进入编辑页面，我们看到我的红框，这表明我们没有 UI\_Group ，那就需要我们添加。

![](/assets/snipaste_20171026_021909.png)

进入 UI\_Group 的编辑页面，将“Name”设置为“weather”，并点击右侧的笔，添加 UI\_Tab 

![](/assets/snipaste_20171026_022227.png)

我们将我们要用的 UI\_Tab 的名称设置为“weather”，并点击添加。

![](/assets/snipaste_20171026_022404.png)

我们发现 UI\_Tab 已经自动更新为我们刚刚设置的“weather”了，那么也可以点击“添加”

![](/assets/snipaste_20171026_022528.png)

此时，我们发现我们的“group”栏目中已经变化成了“weather\[weather\]”，这说明我们刚刚配置的UI信息都生效了。看到“Range”一栏，这是我们温度的范围，由于现在是秋天，我设置为 10~30 摄氏度，下面的“color gradient”可以配置颜色，比如温度越高颜色越红，在看我们的“Name”一栏，还是同样道理，这个名字将会方便你区分节点！全部配置完成之后，我们点击右上角的“完成”。

![](/assets/snipaste_20171026_022748.png)

我们看到这个仪表盘节点的名称已经从“Gauge”变成了“tmp”，我们将“tmp”“Function”节点和“tmp”仪表盘用线连接起来。

![](/assets/snipaste_20171026_023140.png)

好了，我们布置完了第一串节点，让我们点击右上角的“部署”吧！如果你所有步骤都 step by step，相信你会在顶部跳出部署成功的提示！

![](/assets/snipaste_20171026_023644.png)

看到浏览器最右侧，点击“Dashboard”菜单栏，然后点击下方的类似分享的按钮，此时将跳出我们显示效果界面

![](/assets/snipaste_20171026_023747.png)

我们看到这样一个仪表板显示在浏览器上，但是会发现用户体验很差，用户根本不能弄明白这是什么数据，那我们回去修改一下！

![](/assets/snipaste_20171026_024317.png)

双击“tmp”仪表盘，在“Label”一栏写`temperature`，在“Units”一栏写`摄氏度`或者`℃`，之后依次点击“完成”和“部署”，并打开刚刚的Dashboard显示效果页面。

![](/assets/snipaste_20171026_024644.png)

相信你已经做好了和我一样的显示效果！

![](/assets/snipaste_20171026_025000.png)

好了！到这里，你已经完成了`温度`这一串节点的布置，接下来为了建设一个气象显示台，你需要接收并显示出体感温度、相对湿度、降水量、气压、以及风速，让我们一起进入下一个环节吧！






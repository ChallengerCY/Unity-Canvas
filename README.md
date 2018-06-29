# Unity-Canvas

***Canvas***
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp在Unity中，所有的UI元素都绘制在Canvas下面,Canvas是一个携带Canvas组件的GameObject，所有的UI元素都是Canvas的子物体。创建一个UI元素(类似于 GameObject > UI > Image)，如果当前不存在Canvas，会自动创建一个Canvas，之前创建的UI元素则会成为当前Canvas的子物体。Canvas在场景视图中以矩形形状显示，这使得UI元素的定位可以变得简单，而不需要让游戏视图一直可见。Canvas可以使用EventSystem System来帮助实现Messaging System。

**绘制元素的层级**
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UI元素在Canvas中的绘制顺序和在Hierarchy中相同，第一个元素绘制在第一位，紧接着绘制第二个，以此类推。如果两个UI覆盖，则后面的UI会覆盖前面的UI。想要改变UI元素的绘制顺序，只需要在Hierarchy面板中拖动他们来修改。绘制顺序同样可以通过脚本控制Transform component来进行改变:SetAsFirstSibling（第一个）, SetAsLastSibling（最后一个）, 还有 SetSiblingIndex（中间）。

**渲染模式**
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Canvas有三种渲染模式来决定Canvas是渲染到屏幕空间还是世界空间

**Screen Space - Overlay**

![Screen Space - Overlay](https://github.com/ChallengerCY/Unity-Canvas/blob/master/TestCanvas/Picture%26GIF/Screen%20Space%20-%20Overlay.gif)

>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这种模式下的UI始终会渲染到屏幕的最前端，如果屏幕的分辨率发生变化，则Canvas会自适应去匹配屏幕。

**Screen Space - Camera**

![Screen Space-Camera](https://github.com/ChallengerCY/Unity-Canvas/blob/master/TestCanvas/Picture%26GIF/Screen%20Space%20-%20Camera.gif)

>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这种模式类似于Screen Space - Overlay模式，在这个渲染模式下，Canvas被放置到一个渲染其摄像机的指定位置。UI元素都是由这个指定的摄像机绘制，意味着摄像机的设置会影响UI的外观。在Canvas设置成Perspective模式时，UI会以Perspective模式渲染，可以通过控制Field of View来控制perspective distortion的数值。如果屏幕发生分辨率，大小发生变化，或者摄像机的摄像区域发生变化，Cavnas会自适应变化。

**World Space**

![World Space](https://github.com/ChallengerCY/Unity-Canvas/blob/master/TestCanvas/Picture%26GIF/World%20Space.gif)

>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在这个模式下，Canvas将会作为一个物体存在于场景当中，Canvas的大小可以通过 Rect Transform来调整，UI元素以3d布局的模式来呈现在其他物体之间，这种设定适合于将UI元素放置到世界中，与其他物体进行结合，而不再是一个单纯的屏幕展现的UI元素。 这里有个Event Camera,如果Event Camera为Null，则默认摄像机为Main Camera。

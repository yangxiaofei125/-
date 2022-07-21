## 渐变色 gradient 用法

#### 1.background-color: gradient( linear, 0% 0%, 0% 0%, from( #504737 (棕)), to( #374969（蓝） ) );

![image-20220719103820782](C:\Users\小新\AppData\Roaming\Typora\typora-user-images\image-20220719103820782.png)

#### 2.background-color: gradient( linear, 100% 0%, 0% 0%, from( #504737 ), to( #374969 ) );

![image-20220719103859597](C:\Users\小新\AppData\Roaming\Typora\typora-user-images\image-20220719103859597.png)

#### 3.background-color: gradient( linear, 0% 100%, 0% 0%, from( #504737 ), to( #374969 ) );

![image-20220719103955157](C:\Users\小新\AppData\Roaming\Typora\typora-user-images\image-20220719103955157.png)

#### 4.background-color: gradient( linear, 0% 0%, 100% 0%, from( #504737 ), to( #374969 ) );

![image-20220719104028166](C:\Users\小新\AppData\Roaming\Typora\typora-user-images\image-20220719104028166.png)

#### 5.background-color: gradient( linear, 0% 0%, 0% 100%, from( #504737 ), to( #374969 ) );

![image-20220719104123869](C:\Users\小新\AppData\Roaming\Typora\typora-user-images\image-20220719104123869.png)

## 给一个版添加一个class样式

panel.SetHasClass("className", true/false )

## 交换位置 MoveChildBefore(lastChild, firstChild);

把 lastChild 挪到 firstChild 前面

#### MoveChildBefore(lastChild, firstChild)

把 lastChild 挪到 firstChild 后面

#### MoveChildAfter(lastChild, firstChild)

## transition 与animation中的如果同时作用于同一个panel上，transition就不生效

```
.anim_floating{
	animation-name: float;
  	animation-duration: 3s;
  	animation-timing-function: linear;
  	animation-iteration-count: infinite; 
}

@keyframes 'float' {
  0% {
    transform:  translateY(0px) scale3d(1, 1, 1);
  }
  50% {
    transform:  translateY(10px) scale3d(1, 1, 1);
  }
  100% {
    transform:  translateY(0px) scale3d(1, 1, 1);
  }
}
.new_hero_lihui_-1 {
	opacity: 0;
	transform: translateX(-500px);
}
<Panel id="new_hero_lihui" class="new_hero_lihui anim_floating">
</Panel>
```

此时 new_hero_lihui 这个版上已经有修改 transform 的动画了，所以此时在js中给new_hero_lihui加上.new_hero_lihui_-1 这个类
这个类里的transform也不会生效

### 如果此时想这个元素既可以用anim_floating这个动画也得实现transfrom的位置变动的话，就需要考虑这两个操作需不需要同时进行，如果不需要同时进行那就需要在移动位置时把animation的class去掉，确保位置移动操作结束（加Schedule），再把animation加上
# css 记录

--------------------

## 1. 纯 css 实现 打字效果

```html
  <div class="typing">
    <div class="typing-effect">Typing effect for text</div>
  </div>
```

```css
.typing {
  height: 80vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.typing-effect {
  /*
  ch 等于 一个 0 的宽度 1ch = 1个英文 = 1个数字 2ch = 1个中文
    ch 是一个相对单位，所谓相对，意思是 ch 会根据当前容器的 ****font-size**** 变化而变化
  */
  width: 22ch; 
  white-space: nowrap;
  overflow: hidden;
  border-right: 3px solid;
  font-family: monospace;
  font-size: 2em;
  animation: typing 6s steps(22) infinite, effect .5s step-end infinite alternate;
}

@keyframes typing {
  from {
    width: 0;
  }

  50% {
    width: 22ch;
  }
  to {
    width: 22ch;
  }
}

@keyframes effect {
  50% {
    border-color: transparent;
  }
}
```

### 相关知识

- `ch` 这是一个 css 单位。`ch` 等于 一个 0 的宽度。
  相应公式:
    1. `1ch = 1个英文 = 1个数字`
    2. `2ch = 1个中文`
  ch 是一个相对单位，所谓相对，意思是 ch 会根据当前容器的 ****font-size**** 变化而变化（这样可以用 ch 做很多效果了）
- `animation` 一个 css 做动画的属性。
  1. `animation-name: string | 'none'`： 使用 `@keyframes` 关键字来创建的动画名字。
  2. `animation-duration: number`：动画指定需要多少秒或毫秒完成，如果为 0 的话就没有动画效果了。
  3. ```
      animation-timing-function:
      
      // 都是连续的
      linear(动画从头到尾的速度是相同的)
      ease(默认。动画以低速开始，然后加快，在结束前变慢)
      ease-in(动画以低速开始)
      ease-out(动画以低速结束)
      ease-in-out(动画以低速开始和结束)
      cubic-bezier(n,n,n,n) (贝塞尔曲线， 上面的几个都是贝塞尔曲线的简化)
      
      // 都是断断续续的
      steps(number, start | end)
      (两个参数， 第一个为整数，表示把我们的动画分成了多少段, 第二个参数表示 动画执行节点。 start 代表在段结束时执行动画， end 代表在段开始时执行动画。)
      step-start( steps 函数的简化,  等同于 `steps(1, start)` )
      step-end( steps 函数的简化,  等同于 `steps(1, end)` )
      
     ```
     ： 指定动画将如何完成一个周期
    4. `animation-delay: number` （单位可以是 s 或者 ms）, 2s 表示 动画再2s 后开始， -2s 表示动画马上开始， 但是会 跳过2s 中， 假如一段动画是4s ，则会立即从 2s 的阶段开始。
    5. `animation-iteration-count: number | infinite` (表示动画播放几次 或 无限(infinite)次)
    6. `animation-direction: normal | reverse | alternate | alternate-reverse | initial | inherit` （定义是否循环交替反向播放动画）
        normal: 默认值。动画按正常播放。
        reverse: 动画反向播放。
        alternate: 动画在奇数次（1、3、5...）正向播放，在偶数次（2、4、6...）反向播放。
        alternate-reverse: 动画在奇数次（1、3、5...）反向播放，在偶数次（2、4、6...）正向播放。
     7. `animation-fill-mode: none | forwards | backwards | both | initial | inherit`
    （这个相对比较难理解， 但是将上面的打字动画 animation 值变成 animation: typing 6s steps(22) 0.5s 1 reverse backwards, effect .5s step-end infinite alternate;）
     这样你大概就能理解了
     none 表示 在动画结束后，元素的表现将是 初始时的表现。 何为初始状态，你要理解 初始状态和 `0%` `20%` `100%` 帧的状态是不一样的。
     forwards 表示 在动画结束后，元素的表现将是结束时的表现。也就是对应 `keyframe` 中的 `to` 或者 `100%` 帧。
     backwards 表示 在动画结束后， 元素的表现将是开始时的表现。也就是对应 `keyframe` 中的 `from` 或者 `0%` 帧。
     both 表示动画遵循 forwards 和 backwards 的规则。表示：动画开始之前是 `from` 或 `0%` 关键帧；动画完成之后是 `to` 或 `100%` 关键帧状态。
     8. `animation-play-state: paused | running`  表示动画是否停止还是运动，可以类似于视频一样控制播放动画还是停止动画。
        
        
        
        
        
        

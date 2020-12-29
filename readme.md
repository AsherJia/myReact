# 需求

> Promise States

- 2.1.1 当pending的时候，一个promise可能转换成fulfilled或者rejected状态
- 2.1.2 当fulfilled的时候，一个promise
    - 一定无法转换成其他状态
    - 一定有一个无法转换的值
- 2.1.3 当rejected的时候
    - 一定无法转换成其他状态
    - 一定有一个原因，并且无法改变

> The `then` Method

```javascript

promise.then(onFulfilled, onRejected)

```

- 2.2.1 如果onFulfilled和onRejected不是一个function,则忽略
- 2.2.2 如果onFulfilled是一个function
    - 它需要在promise fulfilled状态后被调用，第一个参数是promise value值
    - 它不能在fulfilled之前调用
    - 它只能被调用一次
- 2.2.3 如果onRejected是一个function
    - 他需要在promise rejected状态后被调用，第一个参数是promise reason值
    - 它不能再rejected之前调用
    - 它只能被调用一次
- 2.2.4 onFulfilled or onRejected must not be called until the execution context stack contains only platform code. [3.1].
- 2.2.5 onFulfilled 和 onRejected 必须以方法的形式调用。
- 2.2.6 then可能会在一个promise中调用多次
    - 
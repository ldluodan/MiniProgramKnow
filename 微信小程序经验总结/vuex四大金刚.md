## 个人的理解是全局状态管理更合适；简单的理解就是你在state中定义了一个数据之后，你可以在所在项目中的任何一个组件里进行获取、进行修改，并且你的修改可以得到全局的响应变更
### vuex 四大金刚
##### 1.State

```
 我们要把我们需要做状态管理的量放到这里来，然后在后面的操作动它
 const state = { 
         blogTitle: '迩伶贰blog',
         views: 10,
         blogNumber: 100,
         total: 0,
         todos: [
         {id: 1, done: true, text: '我是码农'},
         {id: 2, done: false, text: '我是码农202号'},
         {id: 3, done: true, text: '我是码农202号'}
         ]
    }
```
#### 2. Mutation

```
任何不以mutation的方式改变state的值，都是耍流氓（违法）
    const mutation = {
         addViews (state) {
         state.views++
         },
         blogAdd (state) {
         state.blogNumber++
         },
         clickTotal (state) {
         state.total++
         }
    }
```
#### 3.Action

```
action 的作用跟mutation的作用是一致的，它提交mutation，从而改变state，是改变state的一个增强版
const actions = {
         addViews ({commit}) {
         commit('addViews')
         },
         clickTotal ({commit}) {
         commit('clickTotal')
         },
         blogAdd ({commit}) {
         commit('blogAdd')
         }
    }
```
#### 4.Getter
```
有时候我们需要从 store 中的 state 中派生出一些状态，例如对列表进行过滤并计数。减少我们对这些状态数据的操作
```


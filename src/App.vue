<template>
    <!-- vue2.0 需要根元素  vue3.0 可以是代码片段 fragment -->
    <div>
        <!--1.1 使用A模块的state数据 -->
        <p>{{$store.state.moduleA.username}}</p>
        <!--1.2 使用A模块的getters数据 -->
        <p>{{$store.getters.newName}}</p>
        <!--2.1 使用B模块的state数据  -->
        <p>{{$store.state.moduleB.username}}</p>
        <!--2.2 使用B模块的getters数据  -->
        <p>{{$store.getters['moduleB/newName']}}</p>
        <hr>
        <button @click="mutationsFn">mutationsFn</button>
        <button @click="actionsFn">actionsFn</button>
    </div>
</template>
<script>
import { useStore } from 'vuex'

export default {
  name: 'App',
  setup () {
    const store = useStore()
    const mutationsFn = () => {
      // 2.3提交B模块的修改
      store.commit('moduleB/updateName')
    }
    const actionsFn = () => {
      // 2.4调用B模块的action
      store.dispatch('moduleB/updateName')
    }
    return { mutationsFn, actionsFn }
  }
}

</script>

# 常用条件渲染

### v-for

```
v-for="(item,index) in list"
```
### v-model
```
// 通过v-model把数据绑定到控件上
v-model="listQuery.storeId
```
### v-if v-else-if v-else

```
v-if="flag"

v-else-if = "flag2"

v-else
```


# 组件生命周期、和所需的属性
```
  // 每个组件需要保持长连接所需的key
  name: 'ProductStockList', 
  // 页面用到的组件
  components: { BackToTop, Pagination },
  // 计算画面所需内容，有缓存作用
  computed: {
    ...mapGetters([
      'member'
    ])
  },
  // 画面作用域数据存储位置
  data() {
    return {
      list:[]
    }
  },
  // 页面被创建，画面对象还未生成
  created() {
    // 初始化画面信息
    this.init()
  },
  // 其他生命周期 
  // beforeCreate 组件创建前，这个状态数据、方法没有
  // beforemount 只能拿到跟节点
  // mounted 当前阶段能获取数据和方法，可以做写操作
  // beforeUpdate 数据更新，但是画面没生成虚拟节点
  // updated 根据数据渲染完成
  // beforeDestroy 销毁前
  // destroyed 销毁后
  // 画面作用域方法
  watch:{
    form.name(newVal,oldVal){
        //监控name字段
    }
  },
  methods: {
    init() {
      // 获取路由中的参数
      const query = this.$route.params
    },
    otherFunc() {
      // .......
    }
  },
  ```
# cvshq常用脚本

1、打开新的页面
```
// name: 'ProductStockDetail' 表示需要跳转画面的路由
// params 里面防止所需要的参数。 注: id和primary 必须要，单页面多tab需要依赖唯一标志
this.$router.push({ name: 'ProductStockDetail'  params: { row: this.row, id: `${this.row.productId}-${this.row.storeId}` , primary: `查看-${this.row.productId}-${this.row.storeId}` }})
```
2、获取跨页面参数
// 获取路由中的参数
const query = this.$route.params

3、API请求
```
apiService(condition).then(response => {
  // 成功返回
}).catch(err => {
  // 失败
})
```

4、权限（只需要做按钮权限就行，页面权限底层已实现）
```
// 每个标签增加
 v-permission="'ProductListCreate'"
```

5、标签点击事件

```
@click="handleFunction"
```























